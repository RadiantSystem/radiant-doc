---
lang: en
lang-ref: tickets-get-articles
title: "RS4OTRS_API: tickets/getArticles"
---

### Get articles

**/tickets/getArticles**

Need permissions: RO, RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- TicketID - ticket id.

Optional parameters:

- Count - just article count.
- IsVisibleForCustomer - 0\|1
- Order - ASC \| DESC
- Limit - limit.
- Page - page of article result set.

Successful answer (article count):

```
{
    "Response": "OK",
    "Count": 5
}
```

Successful answer:

```
{
    "Articles": [{
        "Seen": 1,
        "Age": 6627369,
        "PriorityID": 3,
        "ContentType": "text/plain; charset=utf-8",
        "ServiceID": null,
        "StateID": 4,
        "Body": "asdfasdf",
        "EscalationTime": null,
        "CreateTime": "2019-06-16 04:23:53 (Europe/Moscow)",
        "Changed": "2019-06-16 00:23:59",
        "OwnerID": 1,
        "CommunicationChannelID": 2,
        "Owner": "root@localhost",
        "Created": "2019-06-16 04:23:53 (Europe/Moscow)",
        "ArticleID": 341,
        "QueueID": 2,
        "ReplyTo": null,
        "HTMLBody": {
            "ContentAlternative": null,
            "ContentID": null,
            "Disposition": "inline",
            "ContentType": "text/html; charset=\"utf-8\"",
            "Filename": "file-2",
            "FilesizeRaw": 202,
            "FileID": 1
        },
        "CreateBy": 1,
        "TicketID": 266,
        "CreateTimeServer": "2019-06-16 00:23:53",
        "ChangeTime": "2019-06-16 04:23:53 (Europe/Moscow)",
        "Cc": null,
        "EscalationResponseTime": 0,
        "UnlockTimeout": 0,
        "IncomingTime": 1560644633,
        "Charset": "utf-8",
        "ArchiveFlag": "n",
        "Bcc": null,
        "CustomerUserID": null,
        "Attachments": [],
        "Type": "Incident",
        "ContentCharset": "utf-8",
        "Responsible": "root@localhost",
        "SenderType": "customer",
        "ChangeTimeServer": "2019-06-16 00:23:53",
        "ResponsibleID": 1,
        "ChangeBy": 1,
        "MimeType": "text/plain",
        "Subject": "vxcvzv",
        "InReplyTo": null,
        "RealTillTimeNotUsed": 0,
        "GroupID": 1,
        "CustomerID": null,
        "MessageID": null,
        "TypeID": 2,
        "To": "Raw",
        "Priority": "3 normal",
        "Avatar": "https://www.shareicon.net/...512.png",
        "UntilTime": null,
        "EscalationUpdateTime": 0,
        "Queue": "Raw",
        "SenderTypeID": 3,
        "ToRealname": "Raw",
        "State": "open",
        "Title": "vxcvzv",
        "CreatedTimeUnix": 1560633833,
        "References": null,
        "ArticleType": "phone",
        "StateType": "open",
        "IsVisibleForCustomer": 1,
        "FromRealname": "Ivan Testov",
        "EscalationSolutionTime": 0,
        "LockID": 1,
        "TicketNumber": 2019061665000017,
        "ArticleNumber": 1,
        "Lock": "unlock",
        "SLAID": null,
        "From": "\"Ivan Testov\" <iv@test.com>",
        "Direction": "Internal"
    }],
    "Response": "OK"
}
```

No ticket:

```
{
    "Response": "ERROR",
    "Message": "No ticket"
}
```

No permission ``ro'' or ``rw'' on a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Direction:

- Internal for internal messages.
- Incoming for customer messages.
- Outgoing for others (agent, system).
