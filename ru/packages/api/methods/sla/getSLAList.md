---
lang: ru
lang-ref: sla-get-sla-list
title: "RS4OTRS_API: sla/getSLAList"
---

### Get SLA list

**/sla/getSLAList**

Returns SLA list.

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- ServiceID - service id.

Successful answer:

```
{
    "SLAList": [{
        "ID": 1,
        "Title": "BarFoo"
    }],
    "Response": "OK"
}
```
