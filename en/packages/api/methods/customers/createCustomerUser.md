---
lang: en
lang-ref: customers-create-customer-user
title: "RS4OTRS_API: customers/createCustomerUser"
---

### Create customer user

**/customers/createCustomerUser**

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Firstname - first name.
- Lastname - last name.
- CustomerID - CustomerID.
- Login - login.
- Email - email.

Unrequired parameters:

- Password - password.
- Country - country.
- City - city.
- Street - street.
- Zip.
- Phone.
- Mobile.
- Fax.
- Title.
- Comment.
- InterfaceLanguage - ru, en etc.

Successful answer:

```
{ "Response": "OK" }
```

Without required parameters:

```
{
    "Message": "Required fields is not defined: Firstname, Lastname, CustomerID, Login, Email",
    "Response": "ERROR"
}
```

Cannot create a customer user:

```
{
    "Response": "ERROR",
    "Message": "Couldn't create customer user"
}
```
