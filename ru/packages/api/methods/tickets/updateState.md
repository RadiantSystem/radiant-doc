---
lang: ru
lang-ref: tickets-update-state
title: "RS4OTRS_API: tickets/updateState"
---

### Update state

**/tickets/updateState**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- State - state or
- StateID - state id.
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
    "Message": "Cannot update State"
}
```

You are not an Owner:

```
{
    "Response": "ERROR",
    "Message": "You must be an owner of the ticket"
}
```

Cannot unlock closed Ticket:

```
{
    "Response": "ERROR",
    "Message": "State has been changed but couldn't unlock Ticket"
}
```
