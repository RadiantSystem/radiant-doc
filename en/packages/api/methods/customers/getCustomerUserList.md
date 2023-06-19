---
lang: en
lang-ref: customers-get-customer-user-list
title: "RS4OTRS_API: customers/getCustomerUserList"
---

### Get customer user list

**/customers/getCustomerUserList**

Required parameters:

| **Name** | **Description** |
| The value of "SessionName" field of /auth/login response | main token |

Optional parameters:

| **Name** | **Description** |
| Search | value for other fields of a customer user |
| Login | a customer user login |
| Email | a customer user email |
| CustomerID | CustomerID of a customer user |
| Limit | limit for result items |

Successful answer:

```
{
    "CustomerUsers": [{
        "CustomerUser": "RS",
        "Lastname": "bbb",
        "Firstname": "aaa",
        "Avatar": "http://www.sg-webs.com/wp-...-Circle.png",
        "Login": "zzbbb",
        "Email": "zzbvvvf@qqqzzz.com",
        ...
        "DynamicField_ABC": "FFF"  # added in Config.pm in CustomerUser
                                   # Map section
    }, {
        "CustomerUser": "ABC",
        "Lastname": "Test",
        "Firstname": "Testov",
        "Avatar": "http://www.sg-webs.com/wp-...-Circle.png",
        "Login": "test",
        "Email": "testtest@teststadsasdf.com",
        ...
        "DynamicField_ABC": "FFF"  # added in Config.pm in CustomerUser
                                   # Map section
    }],
    "Response": "OK"
}
```

Avatar - url stub by default.
