---
lang: en
lang-ref: auth-lost-password
title: "RS4OTRS_API: auth/lostPassword"
---

### Reset password

**/auth/lostPassword**

Required parameters:

- User  - user login.
- Token - token from an email when we click on the link "Lost password"
          on the login page in OTRS.

Successful answer. In case of valid users or for fake ones for the security
sake:

```
{
    "Message": "Sent password reset instructions. Please check your email.",
    "Response" : "OK"
}
```

In case of click on a correct link from a mail:

```
{
    "Message": "Sent new password to 'UserName'. Please check your email.",
    "Response" : "OK"
}
```

In case of disabled config option "LostPassword":

```
{
    "Message": "Feature not active.",
    "Response": "ERROR"
}
```

In case of error while sending email with instructions or with a new password:

```
{
    "Message": "Please contact the administrator.",
    "Response": "ERROR"
}
```

In case of invalid token when a user go to a reset link from a mail:

```
{
    "Message": "Invalid token.",
    "Response": "ERROR"
}
```
