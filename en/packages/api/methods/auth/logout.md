---
lang: en
lang-ref: auth-logout
title: "RS4OTRS_API: auth/logout"
---

### Logout

**/auth/logout**

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- ChallengeToken - additional token.

Successful answer:

```
{
    "Message": "Logout successful.",
    "Response": "OK"
}
```

Unsuccessful answer. In case of incorrect ChallengeToken:

```
{
    "Response": "ERROR",
    "Message": "Invalid Challenge Token!"
}
```

In case of error while removing session:

```
{
    "Response": "ERROR",
    "Message": "Can`t remove SessionID."
}
```
