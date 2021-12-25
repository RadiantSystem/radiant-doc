---
lang: ru
lang-ref: test-email
title: Подготовка письма для проверок
---

Подготавливаем письмо для шифрования:

```
echo "From: unittest@example.org" >> test-email.txt
echo "To: unittest@example.com" >> test-email.txt
echo "Subject: Unittest" >> test-email.txt
echo >> test-email.txt
echo -n "Hi" >> test-email.txt
```

Подписываем письмо:

```
openssl smime -sign \
  -in test-email.txt \
  -out signed-test-email.txt \
  -signer SMIMECertificate-1.asc \
  -inkey SMIMEPrivateKey-1.asc
```

и шифруем:

```
openssl smime -encrypt \
  -binary -des3 \
  -in signed-test-email.txt \
  -out encrypted.txt SMIMECertificate-1.asc
```

Заполняем пробное письмо в scripts/test/sample/SMIME/SMIME-Test.eml:

```
cat SMIME-Test.eml

To: unittest@example.org
Date: Tue, 24 May 2016 09:42:01 +0200
From: unittest@example.org
X-Mailer: Radiant Mail Service (5.0.x git)
Subject: Unittest data
X-Powered-BY: Radiant (https://radiantsystem.com/)
Message-ID: <1464075721.417156.319608702@localhost>
```

Дописываем зашифрованное письмо в пробное:

```
cat encrypted.txt >> SMIME-Test.eml
```
