---
lang: ru
lang-ref: tickets-update-pending-time
title: "RS4OTRS_API: tickets/updatePendingTime"
---

### Update pending time

**/tickets/updatePendingTime**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- UntilTimeDateUnix - unix time or
- Year - year.
- Month - month.
- Day - day.
- Hour - hour.
- Minute - minute.
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
    "Message": "Cannot update PendingTime"
}
```
