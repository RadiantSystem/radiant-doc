---
lang: en
lang-ref: tickets-update-customer
title: "RS4OTRS_API: tickets/updateCustomer"
---

### Update customer

**/tickets/updateCustomer**

Need permissions: RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- CustomerID - customer.
- CustomerUserID - customer user login.
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

No permission "rw" on a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Error while update Customer:

```
{
    "Response": "ERROR",
    "Message": "Cannot update Customer"
}
```
