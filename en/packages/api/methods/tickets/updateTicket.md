---
lang: en
lang-ref: tickets-update-ticket
title: "RS4OTRS_API: tickets/updateTicket"
---

### Update ticket

**/tickets/updateTicket**

Need permissions: MOVE\_INTO, OWNER, PRIORITY, RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token
- TicketID - ticket id.

Unrequired parameters:

- Title - title.
- Queue - queue or
- QueueID - queue id.
- Type - type or
- TypeID - type id.
- Service - service or
- ServiceID - service id.
- SLA - SLA or
- SLAID - SLA ID.
- CustomerID - customer.
- CustomerUserID - customer user login.
- Lock - lock.
- LockID - lock id.
- ArchiveFlag - archive flag.
- State - state or
- StateID - state id.
- NewOwner - new owner or
- NewOwnerID - new owner id.
- NewResponsibleUser - new responsible user or
- NewResponsibleUserID - new responsible user id.
- Priority - priority or
- PriorityID - priority id.
- UntilTimeDateUnix - pending time in unix-format.
- Year - pending year.
- Month - pending month.
- Day - pending day.
- Hour - pending hour.
- Minute - pending minute.
- Rule - can be ``TicketEdit'' for different algorithms of Owner changing.
- DynamicFields - a hash with pairs DynamicField name : value.

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

No parameters:

```
{
    "Response": "ERROR",
    "Message": "Pass some fields for ticket update: ..."
}
```

Cannot update some fields:

```
{
    "Response": "ERROR",
    "Message": "The follow parameters wasn't updated: Title, SLA ..."
}
```

In case of failed update some fields then the list of them will be returned.
The method udateTicket is a wrapper for corresponded method such as
updateTicket, updateQueue etc but without detailed information about an error
reason.
