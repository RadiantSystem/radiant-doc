---
lang: ru
lang-ref: tickets-update-priority
title: "RS4OTRS_API: tickets/updatePriority"
---

### Update priority

**/tickets/updatePriority**

Need permissions: RW or PRIORITY

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Priority - priority or
- PriorityID - priority id.
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
    "Message": "Cannot update Priority"
}
```

You are not an Owner:

```
{
    "Response": "ERROR",
    "Message": "You must be an owner of the ticket"
}
```
