---
lang: ru
lang-ref: tickets-update-owner
title: "RS4OTRS_API: tickets/updateOwner"
---

### Update owner

**/tickets/updateOwner**

Need permissions: OWNER or RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- NewUser - new owner login or
- NewUserID - new owner login ID.
- TicketID - ticket id.

Optional parameters:

- Rule - can be ``TicketEdit'' for different algorithms of Owner changing.

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

No permission ``owner'' or ``rw'' on a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Cannot update owner:

```
{
    "Response": "ERROR",
    "Message": "Cannot update Owner"
}
```

You are an Owner already:

```
{
    "Response": "ERROR",
    "Message": "'Already you are an owner"
}
```

You are not an Owner:

```
{
    "Response": "ERROR",
    "Message": "You must be an owner of the ticket"
}
```

An onwer is changed but it couldn't change the lock state:

```
{
    "Response": "ERROR",
    "Message": "Cannot lock by a new owner"
}
```
