---
lang: en
lang-ref: tickets-mark-ticket-as-seen
title: "RS4OTRS_API: tickets/markTicketAsSeen"
---

### Mark ticket as seen

**/tickets/markTicketAsSeen**

Need permissions: RO

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Seen - is ticket seen.
- TicketID - ticket id

Successful answer:

```
{
    "Response": "OK"
}
```

No ticket:

```
{
    "Response": "ERROR",
    "Message": "No ticket"
}
```

No ticket:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Errow while marking ticket as seen:

```
{
    "Response": "ERROR",
    "Message": "Couldn't mark ticket as seen"
}
```
