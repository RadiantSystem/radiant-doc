---
lang: ru
lang-ref: tickets-create-ticket
title: "RS4OTRS_API: tickets/createTicket"
---

### Create ticket

**/tickets/createTicket**

Need permissions: CREATE, RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token
- Title - title.
- QueueID - queue id.
- PriorityID - priority id.
- Body - body.

Unrequired parameters:

- TypeID - type id.
- ServiceID - service id.
- SLAID - SLA id.
- ArticleType - article type (Phone by default, Email, Chat, Internal).
- SenderType - sender type (agent, system, customer by default).
- OwnerID - owner agent id.
- Lock - lock.
- To - to.
- Cc - copy.
- ReplyTo - in reply to.
- ContentType - text/plain; charset=utf-8
- CustomerID - customer.
- CustomerUserID - customer user id.
- StateID - state id.
- UntilTimeDateUnix - pending time in unix-format.
- Year - pending year.
- Month - pending month.
- Day - pending day.
- Hour - pending hour.
- Minute - pending minute.
- Estimated - spent time.
- LockByOwner - lock by owner (1\|0).
- DynamicFields - a hash with pairs DynamicField name : value.

Successful answer:

```
{
    "Response": "OK",
    "TicketID": 238
}
```

Lack of reruired parameters:

```
{
    "Response": "ERROR",
    "Message": "Required fields is not defined: Title, QueueID, PriorityID, Body"
}
```

No permission ``create'' or ``rw'' for a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Incorrect queue:

```
{
    "Response": "ERROR",
    "Message": "Queue is incorrect"
}
```

Cannot create ticket:

```
{
    "Response": "ERROR",
    "Message": "Couldn't create ticket"
}
```

Ticket was added but some operations on it are failed:

```
{
    "Response": "ERROR",
    "Message": "Ticket was created but these operations are failed: SetEstimatedTime, LockByOwner, UpdatePendingTime"
}
```

Ticket are created but without an article:

```
{
    "Response": "ERROR",
    "Message": "Cannot add ticket article"
}
```
