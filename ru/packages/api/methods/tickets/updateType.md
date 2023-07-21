---
lang: ru
lang-ref: tickets-update-type
title: "RS4OTRS_API: tickets/updateType"
---

### Update type

**/tickets/updateType**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Type - type or
- TypeID - type id.
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

No permission ``priority'' or ``rw'' on a ticket queue:

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
    "Message": "Cannot update Type"
}
```
