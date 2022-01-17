---
lang: en
lang-ref: tickets-update-lock
title: "RS4OTRS_API: tickets/updateLock"
---

### Lock/unlock ticket

**/tickets/updateLock**

Update ticket lock state and change an owner.

Not recommended, use \textbf{/updateTicket} instead.

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Lock - lock or
- LockID - lock id.
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

No permission ``rw'' on a ticket queue if OwnerID not equals UserID:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Cannot update an owner:

```
{
    "Response": "ERROR",
    "Message": "Ticket was locked but Owner couldn't be changed",
}
```

Cannot update lock state:

```
{
    "Response": "ERROR",
    "Message": "Couldn't update lock state"
}
```
