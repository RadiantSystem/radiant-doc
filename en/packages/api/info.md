---
lang: en
lang-ref: packages-api-info
title: RS4OTRS_API
---

### Introduction

RS4OTRS_API package is used for communication with OTRS server.

### HTTP communication

API supports GET and POST HTTP requests, but for security reason you
should use only POST ones with JSON body (application/json).

### Auth token and permissions

Almost all methods require a special token. It can be taken
from /auth/login call.

Without a token or with incorrect one you get an error:

```
{
    "Response": "ERROR",
    "Message": "Session invalid. Please log in again."
}
```

Some methods are checked for user permissions (Agent groups permissions). For
such calls there is a field ``Need permissions'' with group permissions list in
this manual.

### Error response

Except ``Session invalid.'' there is also another common error response:

```
{
    "Message": "Please contact the administrator.",
    "Response": "ERROR"
}
```

which says that the problem is non-presumable for such case.

### Request examples

POST request for /auth/login:

```
curl -s -X POST
  -H 'Content-Type: application/json' localhost/otrs/api/auth/login
  -d '{"User":"root@localhost", "Password": "kBHsn6"}'
```

GET request:

```
curl -s -X GET
"localhost/bin/api/auth/login?User=root@localhost&Password=kBHsn6"
```

### Methods list

#### /auth

- [/login](/en/packages/api/methods/auth/login)
- [/logout](/en/packages/api/methods/auth/logout)
- [/lostPassword](/en/packages/api/methods/auth/lostPassword)

#### /customers

- [/createCustomerUser](/en/packages/api/methods/customers/createCustomerUser)
- [/getCustomerList](/en/packages/api/methods/customers/getCustomerList)
- [/getCustomerUser](/en/packages/api/methods/customers/getCustomerUser)
- [/getCustomerUserList](/en/packages/api/methods/customers/getCustomerUserList)

#### /filters

- [/getTicketViews](/en/packages/api/methods/filters/getTicketViews)

#### /queues

- [/getQueueList](/en/packages/api/methods/queues/getQueueList)

#### /services

- [/getServiceList](/en/packages/api/methods/services/getServiceList)

#### /settings

- [/getLanguageList](/en/packages/api/methods/settings/getLanguageList)
- [/setPushNotificationToken](/en/packages/api/methods/settings/setPushNotificationToken)

#### /sla

- [/getSLAList](/en/packages/api/methods/sla/getSLAList)

#### /system

- [/getPackageList](/en/packages/api/methods/system/getPackageList)
- [/getDynamicFieldList](/en/packages/api/methods/system/getDynamicFieldList)

#### /tickets

- [/createArticle](/en/packages/api/methods/tickets/createArticle)
- [/createAttachment](/en/packages/api/methods/tickets/createAttachment)
- [/createTicket](/en/packages/api/methods/tickets/createTicket)
- [/getArticles](/en/packages/api/methods/tickets/getArticles)
- [/getAttachment](/en/packages/api/methods/tickets/getAttachment)
- [/getTicketList](/en/packages/api/methods/tickets/getTicketList)
- [/markArticleAsSeen](/en/packages/api/methods/tickets/markArticleAsSeen)
- [/markTicketAsSeen](/en/packages/api/methods/tickets/markTicketAsSeen)
- [/updateArchiveFlag](/en/packages/api/methods/tickets/updateArchiveFlag)
- [/updateCustomer](/en/packages/api/methods/tickets/updateCustomer)
- [/updateLock](/en/packages/api/methods/tickets/updateLock)
- [/updateOwner](/en/packages/api/methods/tickets/updateOwner)
- [/updatePendingTime](/en/packages/api/methods/tickets/updatePendingTime)
- [/updatePriority](/en/packages/api/methods/tickets/updatePriority)
- [/updateQueue](/en/packages/api/methods/tickets/updateQueue)
- [/updateResponsible](/en/packages/api/methods/tickets/updateResponsible)
- [/updateService](/en/packages/api/methods/tickets/updateService)
- [/updateSLA](/en/packages/api/methods/tickets/updateSLA)
- [/updateState](/en/packages/api/methods/tickets/updateState)
- [/updateTicket](/en/packages/api/methods/tickets/updateTicket)
- [/updateTitle](/en/packages/api/methods/tickets/updateTitle)
- [/updateType](/en/packages/api/methods/tickets/updateType)
- [/watchTicket](/en/packages/api/methods/tickets/watchTicket)

#### /users

- [/getUserList](/en/packages/api/methods/users/getUserList)
- [/getUserPermissions](/en/packages/api/methods/users/getUserPermissions)

### Mobile application part

- [Mobile notifications](/en/packages/api/mobile)

### About

- [Changes](/en/packages/api/changes)
