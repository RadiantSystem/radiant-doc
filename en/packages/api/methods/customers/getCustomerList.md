---
lang: en
lang-ref: customers-get-customer-list
title: "RS4OTRS_API: customers/getCustomerList"
---

### Get customer list

**/customers/getCustomerList**

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.

Successful answer:

```
{
    "CustomerCompanies": [{
        "CustomerID": "ABC",
        "Name": "ABC Company"
    }, {
        "CustomerID": "RS",
        "Name": "RS Company"
    }],
    "Response": "OK"
}
```
