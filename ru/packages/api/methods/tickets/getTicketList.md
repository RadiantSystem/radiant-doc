---
lang: ru
lang-ref: tickets-get-ticket-list
title: "RS4OTRS_API: tickets/getTicketList"
---

### Get tickets

**/tickets/getTicketList**

Returns a set of tickets or one ticket.

Need permissions: RO, RW

Required parameters:

| **Name** | **Description** |
| The value of "SessionName" field of /auth/login response | main token. |

Optional parameters:

| **Name**                  | **Description** |
| **Count**                 | just to get ticket count (1\|0) |
| **ViewID**                | view ID (for filtering) |
| **SortBy**                | field list for sorting (array of names) |
| **OrderBy**               | field list for sorting order (array of names) |
| **FullTextSearch**        | string for searching in Subject, Body, From, To, Cc ('\%' sign is used for matching: ''\%hello\%'' for example). |
| **TicketID**              | ticket id. |
| **TicketNumber**          | ticket number. |
| **Title**                 | title. |
| **Queues**                | queue list (array of names). |
| **QueueIDs**              | queue list (array of numbers). |
| **Types**                 | type list (array of names). |
| **TypeIDs**               | type list (array of numbers). |
| **SmartSort**             | 1 (see below). |
| **States**                | state list (array of names). |
| **StateIDs**              | state list (array of numbers). |
| **StateType**             | state type: "Open", “Closed”. |
| **Priorities**            | priority list (array of names). |
| **PriorityIDs**           | priority list (array of numbers). |
| **Services**              | service list (array of names). |
| **ServiceIDs**            | service list (array of numbers). |
| **SLAs**                  | SLA list (array of names). |
| **SLAIDs**                | SLA list (array of numbers). |
| **Locks**                 | lock list (array of names). |
| **LockIDs**               | lock list (array of numbers). |
| **OwnerIDs**              | owner list (array of numbers). |
| **ResponsibleIDs**        | responsible list (array of numbers). |
| **WatchUserIDs**          | watch user list (array of number). |
| **CustomerID**            | customer id. |
| **CustomerUserLogin**     | customer user login. |
| **From**                  | from. |
| **To**                    | to. |
| **Cc**                    | copy. |
| **Subject**               | subject. |
| **Body**                  | body. |
| **Limit**                 | limit. |
| **Offset**                | offset. |
| **DynamicFieldsMode**     | mobile \| all adds DynamicFields field. |
| **CreatedNewerMinutes**   | |
| **CreatedOlderMinutes**   | |
| **CreatedNewerDate**      | |
| **CreatedOlderDate**      | |
| **CreatedNewerDays**      | |
| **CreatedOlderDays**      | |

Successful answer:

```
{
    "NeedTokenUpdate": 1,     # Need to set a new token for mobile push
                              # notification.
    "Response": "OK",
    "Tickets": [{
        "Seen": 1,
        "Age": 6624195,
        "PriorityID": 3,
        "ServiceID": null,
        "Type": "Incident",
        "CreatedServer": "2019-06-16 00:23:53",
        "Responsible": "root@localhost",
        "StateID": 4,
        "ResponsibleID": 1,
        "ChangeBy": 1,
        "EscalationTime": 0,
        "HasWatch": 0,
        "UntilTimeDateUnix": 0,
        "Changed": "2019-06-16 04:23:59 (Europe/Moscow)",
        "OwnerID": 1,
        "RealTillTimeNotUsed": 0,
        "GroupID": 1,
        "Owner": "root@localhost",
        "CustomerID": null,
        "TypeID": 2,
        "Created": "2019-06-16 04:23:53 (Europe/Moscow)",
        "UntilTimeDate": 0,
        "Priority": "3 normal",
        "UntilTime": 0,
        "EscalationUpdateTime": 0,
        "CustomerUserLastname": null,
        "Queue": "Raw",
        "QueueID": 2,
        "State": "open",
        "Title": "vxcvzv",
        "ChangedServer": "2019-06-16 00:23:59",
        "CreateBy": 1,
        "LinkCount": 0,
        "TicketID": 266,
        "CustomerUserFirstname": null,
        "StateType": "open",
        "EscalationResponseTime": 0,
        "UnlockTimeout": 0,
        "EscalationSolutionTime": 0,
        "LockID": 1,
        "TicketNumber": 2019061665000017,
        "ArchiveFlag": "n",
        "CreateTimeUnix": 1560633833,
        "Lock": "unlock",
        "SLAID": null,
        "WatcherCount": 0,
        "CustomerUserID": null,
        "DynamicFields": {
          "TestMulti": {
            "Value": null,
            "Type": "Multiselect",
            "Screens": {
              "AgentMobileTicketStatus": "rw"
            },
            "Name": "TestMulti"
          },
          ...
        }
    }]
}
```

Count of tickets:

```
{
    "NeedTokenUpdate": 0,     # Need to set a new token for android push
                              # notification.
    "Response": "OK",
    "Count": 5
}
```

If SmartSort then tickets are sorted by EscalationSolutionTime with useful
algorithm for agents work.

The order of tickets with straight direction (OrderBy=Up by default):

- Expired. From the most to the least ones.
- Not expired. From the approaching to expired to the least ones.
- Without expire. By age, from old to new ones.

With reverse direction (OrderBy=Down):

- Not expired. From the least to the approaching to expired.
- Expired. From the most to the least ones.
- Without expire. By age, from new to old ones.
