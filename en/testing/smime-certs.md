---
lang: en
lang-ref: smime-certs
title: Подготовка SMIME свидетельств для выполнения проверок
---

Свидетельства для проверок расположены здесь:

```
scripts/test/sample/SMIME
```

Они начинаются на SMIME\*.

Имеют следующие расширения:

- .crt
- .pem
- .asc
- .der
- .p7b
- .pfx
- .key

### Создание свидетельств

Создадим папку, где будут располагаться все наши подготавливаемые свидетельства:

```
mkdir Certs
```

Все дальнейшие действия будем выполнять в ней:

```
cd Certs
```

### Создадим Корневой издатель свидетельств (ИС)

Подготовим необходимые для создания свидетельств папки и файлы:

```
mkdir RadiantCA
cd RadiantCA
mkdir certs crl newcerts private
echo "01" > serial
cp /dev/null index.txt
cp /usr/lib/ssl/openssl.cnf .
```

- index.txt -- список выпущенных свидетельств (изначально пустой).
- serial -- текущее последовательное число.
- openssl.cnf -- файл настроек для openssl (взят тот, который идёт вместе с
  openssl). Исходный openssl.cnf в зависимости от ОС может располагаться в
  разных местах.

index.txt и serial прописаны в openssl.cnf в разделе `[ CA_default ]`:

```
[ CA_default ]

dir   = .
...
database  = $dir/index.txt
serial    = $dir/serial
```

#### Создадим личный ключ:

```
openssl genrsa -des3 -out private/SMIMECAPrivateKey-RadiantCARoot.pem 4096
```

- openssl genrsa -- приказ для создания личного ключа
  [RSA](https://ru.wikipedia.org/wiki/RSA).
- -des3 -- пошаговость для тайнописи [Тройной DES](https://ru.wikipedia.org/wiki/Triple_DES).
- -out -- куда поместим создаваемый ключ.
- 4096 -- размер ключа в битах.

При выполнении попросит ввести (придумать) пропуск.

#### Создадим самоподписанное свидетельство

```
openssl req -new -x509 -nodes -sha1 -days 3650 \
        -key private/SMIMECAPrivateKey-RadiantCARoot.pem \
        -out SMIMECACertificate-RadiantRoot.crt
```

- openssl req -- приказ для создания самоподписанного свидетельства.
- -new -- создаёт запрос для свидетельства.
- -x509 -- вместе с данным ключом -new создаст самоподписанное свидетельство
  вместо запроса для свидетельства.
- -nodes -- без тайнописи.
- -sha1 -- вид пошаговости для перемешивания [SHA1](https://ru.wikipedia.org/wiki/SHA-1).
- -days 3650 -- количество дней в течение которого свидетельство достоверно
- -key -- путь к личному ключу.
- -out -- путь к создаваемому свидетельству.

### Создадим Промежуточный издатель свидетельств (ИС)

Подготовим необходимые для создания свидетельств папки и файлы:

```
mkdir RadiantRD
cd RadiantRD
mkdir certs crl newcerts private
echo "01" > serial
cp /dev/null index.txt
cp /usr/lib/ssl/openssl.cnf .
```

#### Создадим личный ключ

```
openssl genrsa -des3 -out private/SMIMECAPrivateKey-RadiantRD.pem 4096
```

#### Создадим открытый ключ

Для начала создадим [запрос .csr на получение свидетельства](https://en.wikipedia.org/wiki/Certificate_signing_request):

```
openssl req -new -sha1 \
  -key private/SMIMECAPrivateKey-RadiantRD.pem \
  -out SMIMECACertificate-RadiantRD.csr
```

Просмотреть сведения о созданном запросе можно так:

```
openssl asn1parse -i -in SMIMECACertificate-RadiantRD.csr
```

Теперь запросим непосредственно открытый ключ, предварительно настроив
openssl.cnf:

```
[ CA_default ]

dir             = .
certificate     = $dir/SMIMECACertificate-RadiantRD.csr.crt
private_key     = $dir/../RadiantRD/private/SMIMECAPrivateKey-RadiantRD.pem
```

И, непосредственно, получение открытого ключа:

```
mv SMIMECACertificate-RadiantRD.csr ../RadiantCA
cd ../RadiantCA
openssl ca -extensions v3_ca \
  -days 3650 \
  -out SMIMECACertificate-RadiantRD.csr.crt \
  -in SMIMECACertificate-RadiantRD.csr \
  -config openssl.cnf
```

Переносим полученные записи обратно в папку:

```
mv SMIMECACertificate-RadiantRD.csr ../RadiantRD
mv SMIMECACertificate-RadiantRD.csr.crt ../RadiantRD
```

#### Настроим второй промежуточной издатель свидетельств

Подготовим необходимые для создания свидетельств папки и файлы:

```
mkdir RadiantLab
cd RadiantLab
mkdir certs crl newcerts private
echo "01" > serial
cp /dev/null index.txt
cp /usr/lib/ssl/openssl.cnf .
```

#### Создадим личный ключ

```
openssl genrsa -des3 -out private/SMIMECAPrivateKey-RadiantLab.pem 4096
```

#### Создадим открытый ключ

Сначала .csr как и прошлый раз:

```
openssl req -new -sha1 \
  -key private/SMIMECAPrivateKey-RadiantLab.pem \
  -out SMIMECACertificate-RadiantLab.csr
```

Переносим в родительскую папку и переходим в неё:

```
mv SMIMECACertificate-RadiantLab.csr ../RadiantRD
cd ../RadiantRD
```

В текущем openssl.conf в разделе [v3_ca] следует прописать:

```
[v3_ca]

subjectAltName=@alt_emails

[alt_emails]
email.1=unittest4@example.org
email.2=unittest5@example.org
```

#### Получаем открытый ключ

```
openssl ca -extensions v3_ca \
  -days 3650 \
  -out SMIMECACertificate-RadiantLab.csr.crt \
  -in SMIMECACertificate-RadiantLab.csr \
  -config openssl.cnf
```

И перемещаем его обратно:

```
mv SMIMECACertificate-RadiantLab.csr ../Lab
```

### Создадим Пользовательское свидетельство

Подготовим необходимые для создания свидетельств папки и файлы:

```
mkdir User
cd User
mkdir certs crl newcerts private
echo "01" > serial
cp /dev/null index.txt
cp /usr/lib/ssl/openssl.cnf .
```

#### Создадим личный ключ

```
openssl genrsa -des3 -out private/SMIMEPrivateKey-smimeuser1.pem 4096
```

#### Создадим открытый ключ

Сначала .csr:

```
openssl req -new \
  -key private/SMIMEPrivateKey-smimeuser1.pem \
  -out SMIMECertificate-smimeuser1.csr \
  -config openssl.cnf
```

Переносим на подпись:

```
mv SMIMECertificate-smimeuser1.csr ../Lab
cd ../Lab
```

Непосредственно получение ключа:

```
openssl x509 -req \
  -days 3650 \
  -CA cacert.crt \
  -CAkey private/SMIMECAPrivateKey-RadiantLab.pem \
  -CAcreateserial \
  -in SMIMECertificate-smimeuser1.csr \
  -out SMIMECertificate-smimeuser1.crt
```

Переносим полученные файлы обратно:

```
mv SMIMECertificate-smimeuser1.\* User
```

### Перенос полученных ключей по местам для проверок

Напоминаю, папка для проверок расположена здесь:

```
scripts/test/sample/SMIME
```

Собственно, сам перенос и указание тайного слова для ключей, которое было
использовано при их создании:

```
cp RadiantCA/SMIMECACertificate-RadiantRoot.crt scripts/test/sample/SMIME/SMIMECACertificate-RadiantRoot.crt
cp RadiantCA/private/SMIMECAPrivateKey-RadiantCARoot.pem scripts/test/sample/SMIME/SMIMECAPrivateKey-RadiantRoot.pem
echo -n "12345" > scripts/test/sample/SMIME/SMIMECAPrivateKeyPass-RadiantRoot.crt
```

тоже самое для остальных трёх чет ключей.

Таким же образом необходимо будет создать ключи для SMIMECertificate-1.asc,
SMIMECertificate-2.asc и т.п, с последующим переносом в папку для проверок.

Отдельно придётся повторить создание подобных свидетельств для проверок в SMIME.t,
только полученные ключи необходимо будет прописать в SMIME.t явно.

Особым случаем при создании личных ключей можно считать запись вида:

```
$Private{SmimeTest_4} = {
    CertString => '-----BEGIN ENCRYPTED PRIVATE KEY-----
```

в то время как остальные имеют такой вид:

```
    $Private{SmimeTest_3} = {
        CertString => '-----BEGIN RSA PRIVATE KEY-----
```

Так вот, "ENCRYPTED" вид ключа можно получить с помощью следующего приказа:

```
openssl req -newkey rsa:2048 -keyout host.key
```

### Преобразование ключей и свидетельств в другие расширения

В .pfx:

```
openssl pkcs12 -export \
  -out SMIMECertificate-1.pfx \
  -inkey SMIMEPrivateKey-1.asc \
  -in SMIMECertificate-1.asc
```

В .p7b:

```
openssl crl2pkcs7 -nocrl \
  -out SMIMECertificate-1.p7b \
  -certfile SMIMECertificate-1.asc
```

В .der:

```
openssl x509 -outform der \
  -in SMIMECertificate-1.asc \
  -out SMIMECertificate-1.der
```
