---
lang: en
lang-ref: unit-tests
title: Tests
---

### Tests running

Running YAML tests, for example, from `scripts/test/YAML/`

```perl
sudo -u radiant bin/otrs.Console.pl Dev::UnitTest::Run --test YAML
```

### Running frontend-tests with Selenium

For running frontend-tests with Selenium at first you should set up
its setting in Kernel/Config:

```perl
$Self->{'SeleniumTestsConfig'} = {
    remote_server_addr  => '192.168.96.1',
    port                => '4444',
    platform            => 'ANY',
    browser_name        => 'firefox'
};
```

Then you have to download Selenium server from
[here](https://www.selenium.dev/downloads/):

Run it with java on you server (its ip must be set in remote_server_addr above):

```
java -jar selenium-server-standalone-3.141.59.jar
```

And finally run frontend-tests:

```
# sudo -u radiant bin/otrs.Console.pl Dev::UnitTest::Run --verbose --test Selenium/Agent/Login
```
