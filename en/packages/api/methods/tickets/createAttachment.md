---
lang: en
lang-ref: tickets-create-attachment
title: "RS4OTRS_API: tickets/createAttachment"
---

### Create attachment

**/tickets/createAttachment**

Need permissions: NOTE or RW or CREATE

Required parameters:

- The value of "SessionName" field of /auth/login response - main token
- TicketID - ticket id or
- ArticleID - article id.
- File:
  - Content - content in base64 format.
  - ContentType - content type.
  - Filename - file name.

Successful answer:

```
{
    "Response": "OK",
    "ContentAlternative": null,
    "ContentID": null,
    "Filesize": "4.6 KB",
    "ContentType" : "application/pdf",
    "FilesizeRaw" : 4722,
    "Disposition  : "attachment",
    "FileID": 3
}
```

Incorrect TicketID:

```
{
    "Response": "ERROR",
    "Message": "Ticket is incorrect"
}
```

Incorrect ArticleID:

```
{
    "Response": "ERROR",
    "Message": "Article is incorrect"
}
```

No Ticket:

```
{
    "Response": "ERROR",
    "Message": "No ticket"
}
```

No permission ``create'' or ``note'' or ``rw'' for a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Internal error:

```
{
    "Response": "ERROR",
    "Message": "Internal error. Please contact administrator!"
}
```

Cannot add attachment:

```
{
    "Response": "ERROR",
    "Message": "Cannot add attachment"
}
```

No parameters:

```
{
    "Response": "ERROR",
    "Message": "No Content, ContentType or Filename parameters"
}
```
