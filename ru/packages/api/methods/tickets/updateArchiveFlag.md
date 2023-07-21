---
lang: ru
lang-ref: tickets-update-archive-flag
title: "RS4OTRS_API: tickets/updateArchiveFlag"
---

### Update archive flag

**/tickets/updateArchiveFlag**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- ArchiveFlag - archive flag.
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

Error while update ArchiveFlag:

```
{
    "Response": "ERROR",
    "Message": "Cannot update ArchiveFlag"
}
```
