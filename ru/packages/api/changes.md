---
lang: ru
lang-ref: packages-api-changes
title: RS4OTRS_API
---

## Changes of API

### 6.44.2 [14.03.22]

- /getUserList: fixed empty string fields to undef.

### 6.44.1 [14.02.22]

- /getArticles, /getTicketList: removed datetime conversion for one datetime
  format.

### 6.44.0 [28.01.22]

- /getTicketList: for Dropdown DynamicFields Value keeps a value of
  DynamicField pair instead of a key.
- /createTicket, /createArticle, /updateTicket, /updatePendingTime:
  PendingTime are set taking into account User TimeZone.
- /system/getDynamicFieldList was added for showing all DynamicFields.
- /createTicket: added DynamicFields field.
- /createArticle: added DynamicFields field.
- /getTicketList: UntilTimeDate field format was changed taking into account
  TimeZone of User.
- /getTicketList: added Name field in DynamicField list.
- /getTicketList: even empty DynamicFields in 'mobile' mode are shown.
- /createTicket, /updateTicket: fixed an error showing of an unnecessary field
  check.

### 6.43.0 [30.08.21]

- Added DynamicFields functionality for /getTicketList, /updateTicket.
- Added DynamicFields settings for mobile screens reading/writing.
- Added Screens field for State items in /getTicketViews with ACL settings.

### 6.42.1 [07.04.21]

- /getUserPermissions added Roles groups in a result, fixed double showing
    Queues in result;
- /getCustomerUserList added placeholders 'Not defined' for UserFirstname,
    UserLastname;
- added using TicketSearch method from RS4OTRS\_AdvancedTicketSearch when
    it is installed for v6.1.24+;
- fixed bug about showing services with more than one unaccessible
    ancestor.

### 6.41.0

- /settings/setPushNotificationToken and token processing works only with
    RS4OTRS\_Mobile package;
- fixed package installation description;
- /user/getUserPermissions fixed permissions result list;
- /queue/getQueueList renamed Title to Name and it is a full name (path)
    now and FullTitle became FullName;
- /system/getPackageList was added;
- added Queue permissions check;
- added group permissions for the API methods;
- /queue/getQueueList added Accessible field;
- ``My Queues'' are the same as Open;
- /auth/login removed OTRSAgentInterface token field by default and
    replaced it on SessionName, SessionValue fields;
- /tickets/createAttachment as a POST method also;
- /service/getServiceList also shows services by default in a system;
- /tickets/updateQueue, /tickets/updatePriority fixed security typos;
- /tickets/createArticle sends Email articles by email;
- string fields which is empty (string) are undefined (null)
    in JSON responses;
- date fields which is empty (string) or zero are undefined (null)
    in JSON responses;
- /tickets/getTicketList added TicketFromFullTextSearch field with
    a ticket information when it is found by FullTextSearch with numbers
    in it which are like TicketNumber of a ticket;
- /tickets/getTicketList SmartSort parameter added for useful sorting by
    EscalationSolutionTime;
- /filter/getTicketViews fixed default Colors when RS4OTRS\_Mobile package
    isn't installed;
- removed useless permission checks;
- /customers/getCustomerUser added error responses.
- /tickets/getTicketList fixed timezone error for CreateTimeUnix field.
- /tickets/getTicketList fixed Count response.
- /tickets/createTicket LockByOwner is true by default.
- My Queues filter gets queues from personal queues of personal
    notification settings of a user.
- /services/getServiceList for CustomerUserLogin returns a tree
    as for /queues/getQueueList.
- /tickets/updateTicket State, Owner, Priority cannot be changed
    ticket a ticket isn't locked by a user.
- /tickets/createAttachment, /tickets/updateOwner,
    /tickets/updatePriority, /tickets/updateQueue,
    /tickets/updateState added errors response.
- /ticket/createArticle fixed a ticket history message.
- /customers/getCustomerUserList added query parameters for searching.
- /tickets/updateTicket, /tickets/updateState closed tickets will be
    unlocked also.
- /tickets/updateTicket, /tickets/updateOwner added Rule parameter for
    different algorithms of Owner changing.
