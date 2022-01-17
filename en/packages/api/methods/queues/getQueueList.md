---
lang: en
lang-ref: queues-get-queue-list
title: "RS4OTRS_API: queues/getQueueList"
---

### Get queue list

**/queues/getQueueList**

Return queues. With RO or RW permissions by default.

Need permissions: RO, CREATE, RW, MOVE_INTO

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.

Optional parameters:

- ForCreateTicket - 0\|1 also show queues from groups with CREATE permissions.
- ForUpdateQueue  - 0\|1 also show queues from groups with MOVE_INTO permissions.

Successful answer:

```
{
    "Queues": [{
        "ID": 1,
        "Name": "Postmaster",
        "FullName": "Postmaster",
        "Accessible": 1
    }, {
        "ID": 5,
        "Name": "Misc2",
        "FullName": "Misc2",
        "Accessible": 1
    }, {
        "ID": 4,
        "Name": "Misc",
        "FullName": "Misc",
        "Accessible": 0
    }, {
        "ID": 3,
        "Name": "Junk",
        "FullName": "Junk",
        "Accessible": 1
    }, {
        "ID": 2,
        "Name": "Raw",
        "FullName": "Junk",
        "Accessible": 1
    }],
    "QueueTree": [{
        "FullName": "Postmaster",
        "ID": 1,
        "Childs": [],
        "Accessible": 1,
        "Name": "Postmaster"
    }, {
        "FullName": "Raw",
        "ID": 2,
        "Childs": [],
        "Accessible": 1,
        "Name": "Raw"
    }, {
        "FullName": "Junk",
        "ID": 3,
        "Childs": [],
        "Accessible": 1,
        "Name": "Junk"
    }, {
        "FullName": "Misc",
        "ID": 4,
        "Childs": [
            {
                "FullName": "Misc2",
                "ID": 5,
                "Childs": [],
                "Accessible": 1,
                "Name": "Misc"
            }
        ],
        "Accessible": 0,
        "Name": "Misc"
    }],
    "Response": "OK"
}
```

- Queues - all queues for User as an array.
- QueueTree - all queues for User as Tree.
- Accessible - 0\|1. Is Queue available for user or not? For integrity of Tree it
is necessary to show parent queues if they aren't available for User at all.
