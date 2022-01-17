---
lang: en
lang-ref: tickets-update-title
title: "RS4OTRS_API: tickets/updateTitle"
---

### Update title

**/tickets/updateTitle**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Title - ticket title.
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
    "Message": "Cannot update Title"
}
```
