---
lang: en
lang-ref: tickets-update-queue
title: "RS4OTRS_API: tickets/updateQueue"
---

### Update queue

**/tickets/updateQueue**

Need permissions: RW for current Queue and MOVE\_INTO for a new One.

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Queue - queue or
- QueueID - queue id.
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

No permission ``move\_into'' ``rw'' on a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

If a ticket is locked and an owner isn't you:

```
{
    "Response": "ERROR",
    "Message": "You must be owner of ticket"
}
```

Cannot update:

```
{
    "Response": "ERROR",
    "Message": "Cannot update Queue"
}
```

You are not an Owner:

```
{
    "Response": "ERROR",
    "Message": "You must be an owner of the ticket"
}
```
