---
lang: en
lang-ref: customers-get-customer-user
title: "RS4OTRS_API: customers/getCustomerUser"
---

### Get customer user

**/customers/getCustomerUser**

Required parameters:

| **Name** | **Description** |
| The value of "SessionName" field of /auth/login response | main token. |
| CustomerUser | customer login |

Successful answer:

```
{
    "ValidID": 1,
    "UserEmail": "cl@rs.ngi",
    "UserComment": "",
    "UserCustomerID": "RS",
    "UserFirstname": "Ivan",
    "UserFax": "",
    "UserTitle": "RS",
    "UserLastname": "Testoviy",
    "UserZip": "",
    "UserStreet": "",
    "UserLogin": "client\_001",
    "Response": "OK",
    "UserPhone": "",
    "UserMobile": "",
    "UserCity": "",
    "UserCountry": "",
    ...
    "DynamicField_ABC": "FFF"  # added in Config.pm in CustomerUser Map section
}
```

No CustomerUser parameter:

```
{
    "Response": "ERROR",
    "Message": "No CustomerUser parameter"
}
```

No CustomerUser:

```
{
    "Response": "ERROR",
    "Message": "No CustomerUser"
}
```
