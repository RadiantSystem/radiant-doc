---
lang: ru
lang-ref: tickets-mark-article-as-seen
title: "RS4OTRS_API: tickets/markArticleAsSeen"
---

### Mark article as seen

**/tickets/markArticleAsSeen**

Need permissions: RO

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.
- Seen - is article seen.
- ArticleID - article id.
- TicketID - ticket id

Successful answer:

```
{
    "Response": "OK"
    "TicketID": 5,
    "TicketSeen": 1
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

Cannot mark:

```
{
    "Response": "ERROR",
    "Message": "Couldn't mark article as seen"
}
```
