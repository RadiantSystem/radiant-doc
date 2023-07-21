---
lang: ru
lang-ref: tickets-get-attachment
title: "RS4OTRS_API: tickets/getAttachment"
---

### Get attachment

**/tickets/getAttachment**

Need permissions: RO, RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token
- TicketID - ticket id and/or
- ArticleID - article id.
- FileID - article id.

Successful answer: a file content.

Incorrect ArticleID or no article html content:

```
{
    "Response": "ERROR",
    "Message": "No article!"
}
```

No permission or no attachment:

```
{
    "Response": "ERROR",
    "Message": "No attachment!"
}
```
