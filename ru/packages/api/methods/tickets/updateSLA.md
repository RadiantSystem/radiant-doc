---
lang: ru
lang-ref: tickets-update-sla
title: "RS4OTRS_API: tickets/updateSLA"
---

### Update SLA

**/tickets/updateSLA**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- SLA - SLA or
- SLAID - SLA ID.
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
    "Message": "Cannot update SLA"
}
```
