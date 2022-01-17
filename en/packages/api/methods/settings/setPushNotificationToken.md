---
lang: en
lang-ref: settings-set-push-notification-token
title: "RS4OTRS_API: settings/setPushNotificationToken"
---

### Set token for Android push notifications

**/settings/setPushNotificationToken**

It doesn't work without a package for android notifications!

Add a token for User to the system.

See also "Mobile notifications".

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Token - token from Android notification library.

Successful answer:

```
{ "Response": "OK" }
```

Error response when package isn't installed:

```
{
    "Response": "ERROR",
    "Message": "RS4OTRS\_Mobile package must be installed!"
}
```

Error response for an empty token:

```
{
    "Response": "ERROR",
    "Message": "Token cannot be empty"
}
```
