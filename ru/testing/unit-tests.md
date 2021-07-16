---
lang: ru
lang-ref: unit-tests
title: Проверки
---

### Запуск проверок

На примере проверок YAML, которые расположены в `scripts/test/YAML/`

```perl
sudo -u radiant bin/otrs.Console.pl Dev::UnitTest::Run --test YAML
```

### Запуск проверок взаимодействия со страницами с помощью "Селениум"

Для запуска проверок взаимодействия со страницами, сперва нужно настроить
"Селениум" добавив записи о нём в в Kernel/Config:

```perl
$Self->{'SeleniumTestsConfig'} = {
    remote_server_addr  => '192.168.96.1',
    port                => '4444',
    platform            => 'ANY',
    browser_name        => 'firefox'
};
```

Затем загрузить "Селениум сервер" [отсюда](https://www.selenium.dev/downloads/):

Запустить его с помощью Явы на своём "сервере" (его "IP" должен быть указан
в remote_server_addr выше):

```
java -jar selenium-server-standalone-3.141.59.jar
```

И наконец запустить проверки взаимодействия со страницами:

```
# sudo -u radiant bin/otrs.Console.pl Dev::UnitTest::Run --verbose --test Selenium/Agent/Login
```
