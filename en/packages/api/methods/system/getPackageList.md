---
lang: en
lang-ref: system-get-package-list
title: "RS4OTRS_API: system/getPackageList"
---

### Get installed package list

**/system/getPackageList**

Get information about API package and Mobile one.

Required parameters:

- The value of "SessionName" field of /auth/login response - main token

```
{
    "Packages": [{
        "Version": "6.37.0",
        "Name": "RS4OTRS_API"
    }, {
        "Version": "6.0.4",
        "Name": "RS4OTRS_Mobile"
    }],
    "Response": "OK"
}
```
