---
lang: ru
lang-ref: services
title: "RS4OTRS_API: services/getServiceList"
---

### Get service list

**/services/getServiceList**

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.

Unrequired parameters:

- CustomerUserLogin - services of a customer user.

Successful answer:

```
{
    "Services": [{
        "ID": 1,
        "Title": "FooBar"
    }],
    "Response": "OK"
}
```

Successful answer for CustomerUserLogin parameter:

```
{
    "Response": "OK",
    "ServiceTree": [
        {
            "Accessible": 1,
            "Childs": [],
            "FullName": "Service example #1",
            "ID": 1,
            "Name": "Service example #1"
        },
        {
            "Accessible": 0,
            "Childs": [
                {
                    "Accessible": 1,
                    "Childs": [],
                    "FullName": "Service example #2::Service example #3",
                    "ID": 3,
                    "Name": "Service example #3"
                }
            ],
            "FullName": "Service example #2",
            "ID": 2,
            "Name": "Service example #2"
        }
    ],
    "Services": [
        {
            "Accessible": 1,
            "FullName": "Service example #1",
            "ID": 1,
            "Name": "Service example #1"
        },
        {
            "Accessible": 0,
            "FullName": "Service example #2",
            "ID": 2,
            "Name": "Service example #2"
        },
        {
            "Accessible": 1,
            "FullName": "Service example #2::Service example #3",
            "ID": 3,
            "Name": "Service example #3"
        }
    ]
}
```
