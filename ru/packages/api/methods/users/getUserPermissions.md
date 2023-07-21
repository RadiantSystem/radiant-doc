---
lang: ru
lang-ref: users-get-user-permissions
title: "RS4OTRS_API: users/getUserPermissions"
---

### Get user groups and queues permissions

**/users/getUserPermissions**

Required parameters:

- The value of "SessionName" field of /auth/login response - main token

```
{
    "Groups": [{
        "ID": 1,
        "Permissions": ["rw"],
        "Queues": [
            {
                "ID": 1,
                "Name": "Postmaster"
            },
            ...
        ],
        "Name": "users"
    }, {
        "ID": 2,
        "Permissions": ["rw"],
        "Queues": [
            {
                "ID": 2,
                "Name": "Raw"
            },
            ...
        ],
        "Name": "admin"
    }, {
        "ID": 6,
        "Permissions": ["rw"],
        "Queues": [],
        "Name": "itsm-change"
    },
    ...
    "Response": "OK"
}
```

On the page "Agent Groups" /otrs/index.pl?Action=AdminUserGroup we can change
group relations for a defined agent.

By default there are seven different types of permissions for actions in defined
groups:

- ro
- move\_into
- create
- note
- owner
- priority
- rw

The changing one of them for defined group will affect on appropriate methods.
