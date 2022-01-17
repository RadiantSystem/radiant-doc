---
lang: en
lang-ref: tickets-create-article
title: "RS4OTRS_API: tickets/createArticle"
---

### Create article

**/tickets/createArticle**

Need permissions: NOTE or RW

Required parameters:

- The value of "SessionName" field of /auth/login response - main token
- TicketID - ticket id.
- Subject - subject.
- Body - body.

Unrequired parameters:

- ArticleType - article type (Phone by default, Email, Chat, Internal).
- SenderType - sender type (agent, system, customer by default).
- OwnerID - owner agent id.
- Lock - lock.
- To - to.
- Cc - cc.
- ReplyTo - in reply to.
- ContentType - text/plain; charset=utf-8
- Charset
- MimeType
- Estimated - spent time.
- State - state.
- StateID - state id.
- UntilTimeDateUnix - pending time in unix-format or
- Year - pending year.
- Month - pending month.
- Day - pending day.
- Hour - pending hour.
- Minute - pending minute.

Successful answer:

```
{
    "Response": "OK",
    "ArticleID": 9382
}
```

Lack of required parameters:

```
{
    "Response": "ERROR",
    "Message": "Required fields is not defined: TicketID, Subject, Body"
}
```

No ticket:

```
{
    "Response": "ERROR",
    "Message": "No ticket"
}
```

No permission ``note'' and ``owner'' or ``rw'' on a ticket queue:

```
{
    "Response": "ERROR",
    "Message": "No permission"
}
```

Article was added but some operations on it are failed:

```
{
    "Response": "ERROR",
    "Message": "Article was created but these operations are failed: SetEstimatedTime, UpdateState, UpdatePendingTime"
}
```

Other errors while adding article:

```
{
    "Response": "ERROR",
    "Message": "Cannot add article"
}
```
