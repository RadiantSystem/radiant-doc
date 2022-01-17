---
lang: en
lang-ref: selenium-tests
title: Selenium Tests
---

### Warning

In case of different paths when your code path is different than Home value you
should make a soft link to a path just like Home.

```
ln -s /path/to/your/radiant /opt/radiant
```

Home is `/opt/radiant` by default.

### How to write Selenium tests .t file

Get Selenium object:

```perl
my $Selenium = $Kernel::OM->Get('Kernel::System::UnitTest::Selenium');
```

Prepare tests frame:

```perl
$Selenium->RunTest(sub {
    ...
});
```

Add preparatory header lines for setting a temporary Config enviroment:

```perl
$Selenium->RunTest(sub {

    my $Helper = $Kernel::OM->Get('Kernel::System::UnitTest::Helper');

    $Helper->ConfigSettingChange(
        Valid => 0,
        Key   => 'Ticket::Frontend::AgentTicketNote###DynamicField',
        Value => 0
    );  

    ...
});
```

Create Test user and login:

```perl
$Selenium->RunTest(sub {
    ...

    my $Language = 'ru';

    my $TestUserLogin = $Helper->TestUserCreate(
        Groups   => [ 'admin', 'users' ],
        Language => $Language,
    ) || die "Did not get test user";

    $Selenium->Login(
        Type     => 'Agent',
        User     => $TestUserLogin,
        Password => $TestUserLogin,
    );

    ...
});
```

Open Radiant Action Module page (e.g: AdminACL):

```perl
$Selenium->RunTest(sub {
    ...

    my $ScriptAlias = $Kernel::OM->Get('Kernel::Config')->Get('ScriptAlias');

    $Selenium->VerifiedGet("${ScriptAlias}index.pl?Action=AdminACL");  

    ...
});
```
