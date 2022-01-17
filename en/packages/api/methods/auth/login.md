---
lang: en
lang-ref: auth-login
title: "RS4OTRS_API: auth/login"
---

### Login

**/auth/login**

Required parameters:

- User - user login.
- Password - user password.

Successful answer:

```
{
    "Response": "OK",
    "Message": "Successful login",

    # TokenNameFromSessionNameValue is used for all
    # other requests as a name of a token with SessionValue
    "SessionName": "SessionName value from SysConfig",

    # main token for requests to API
    "SessionValue": "KWhkYIZhLWOu9ptvPF1zpMYN9W4CuWQD"

    # additional token
    "ChallengeToken": "8TuwMme0pnTzelSEbx81yhb6gK8O076L",

    "Me": {
        "UserLogin": "root@localhost",   # user login
        "Email": "root@localhost",       # user email
        "FirstName": "Admin",            # user first name
        "LastName": "OTRS",              # user last name
        "FullName": "Admin OTRS",        # user full name
        "ID": 1,                         # user id in OTRS
        "Avatar": "string"               # url of user image
    },
    "Settings": {
        "Language": "string"  # selected language in OTRS
    }
}
```

In case of:

- a failed login;
- abscence of user information in a system;
- a failed attempt to create session for a user.

```
{
    "Message"  : "Login failed! Your user name or password was entered incorrectly.",
    "Response" : "ERROR"
}
```
