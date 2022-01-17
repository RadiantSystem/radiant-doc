---
lang: en
lang-ref: tickets-watch-ticket
title: "RS4OTRS_API: tickets/watchTicket"
---

### Watch ticket

**/tickets/watchTicket**

Need permissions: RO

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- TicketID - ticket id.
- Subscribe - 1|0.

Successful answer:

```
{ "Response": "OK" }
```

No TicketID:

```
{
    "Response": "ERROR",
    "Message": "No TicketID"
}
```

No ticket:

```
{
    "Response": "ERROR",
    "Message": "No ticket"
}
```

No permission ``ro'' or ``rw'' on a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Cannot subscribe:

```
{
    "Response": "ERROR",
    "Message": "Could not subscribe to ticket"
}
```

Cannot subscribe:

```
{
    "Response": "ERROR",
    "Message": "Could not unsubscribe from ticket"
}
```
