---
lang: en
lang-ref: tickets-update-responsible
title: "RS4OTRS_API: tickets/updateResponsible"
---

### Update responsible user

**/tickets/updateResponsible**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- NewUser - new responsible user login or
- NewUserID - new responsible user ID.
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
    "Message": "Cannot update Responsible"
}
```
