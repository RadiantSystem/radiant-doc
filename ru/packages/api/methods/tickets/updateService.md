---
lang: ru
lang-ref: tickets-update-service
title: "RS4OTRS_API: tickets/updateService"
---

### Update service

**/tickets/updateService**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Service - service or
- ServiceID - service id.
- TicketID - ticket id.

Successful answer:

```
{ "Response": "OK" }
```

No ticket:

```
{
    "Response": "ERROR",
    "Message": "No ticket"
}
```

No permission ``rw'' on a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Cannot update:

```
{
    "Response": "ERROR",
    "Message": "Cannot update Service"
}
```
