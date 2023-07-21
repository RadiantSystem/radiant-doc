---
lang: ru
lang-ref: filters-get-ticket-views
title: "RS4OTRS_API: filters/getTicketViews"
---

### Получить значение полей заявки для отсеивания

**/fitlers/getTicketViews**

Возвращает справочник значений для:

- Set of tickets (View).
- Priority.
- Type.
- State.
- Type of sort.

All of these values can be used as parameters for other API methods.\\

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.

Unrequired parameters:

- QueueID - queue id. When it is set the Screens field also shows on which
  mobile application screens should be shown State items. The State screen
  mapping are set for Mobile package's setting:

  - Ticket::Frontend::AgentMobileTicketNote
  - Ticket::Frontend::AgentMobileNewTicket
  - Ticket::Frontend::AgentMobileTicketStatus
  - Ticket::Frontend::AgentMobileTicketClose
  - Ticket::Frontend::AgentMobileEditTicket

QueueID is used to get the same stricted State list as used for AgentTicketPhone
page in Web OTRS.

Successful answer:

```
{
    "Groups": [{
        "Items": [{
            "ID": -1,
            "Default": 1,
            "Name": "Assigned to me"
        }, {
            "ID": -2,
            "Name": "My Queues"
        }, {
            "ID": -3,
            "Name": "Open"
        }, {
            "ID": -4,
            "Name": "Closed"
        }, {
            "ID": -5,
            "Name": "New notes"
        }, {
            "ID": -6,
            "Name": "My locked"
        }, {
            "ID": -7,
            "Name": "My watched"
        }],
        "Exclusive": 1,
        "Name": "View"
    }, {
        "Items": [{
            "ID": 1,
            "Default": 0,
            "Name": "1 very low",
            "Color": "#1e0000"
        }, {
            "ID": 2,
            "Default": 0,
            "Name": "2 low",
            "Color": "#b7b7b7"
        }, {
            "ID": 3,
            "Default": 1,
            "Name": "3 normal",
            "Color": "#5bb8a5"
        }, {
            "ID": 4,
            "Default": 0,
            "Name": "4 high",
            "Color": "#f9a46c"
        }, {
            "ID": 5,
            "Default": 0,
            "Name": "5 very high",
            "Color": "#f86868"
        }],
        "Name": "Priority"
    }, {
        "Items": [{
            "ID": 6,
            "BackgroundColor": "#b3b3b3",
            "Abbr": "RFC",
            "Name": "RfC",
            "Color": "#b3b3b3"
        }, {
            "ID": 1,
            "BackgroundColor": "#b3b3b3",
            "Abbr": "UNC",
            "Name": "Unclassified",
            "Color": "#b3b3b3"
        }, {
            "ID": 4,
            "BackgroundColor": "#b3b3b3",
            "Abbr": "SER",
            "Name": "ServiceRequest",
            "Color": "#b3b3b3"
        }, {
            "ID": 3,
            "BackgroundColor": "#b3b3b3",
            "Abbr": "INC",
            "Name": "Incident::Major",
            "Color": "#b3b3b3"
        }, {
            "ID": 2,
            "BackgroundColor": "#889988",
            "Abbr": "INC",
            "Name": "Incident",
            "Color": "#5bb8a5"
        }, {
            "ID": 5,
            "BackgroundColor": "#eeeeee",
            "Abbr": "PRB",
            "Name": "Problem",
            "Color": "#ffffff"
        }],
        "Name": "Type"
    }, {
        "Items": [{
            "ID": 2,
            "BackgroundColor": "#ffffff",
            "Default": 0,
            "OnTicketCreateScreen": 0,
            "Name": "closed successful",
            "Color": "#b3b3b3",
            "Screens": {
                "AgentMobileEditTicket": 1,
                "AgentMobileNewTicket": 1,
                "AgentMobileTicketStatus": 1,
                "AgentMobileTicketNote": 1
            },
        }, {
            "ID": 3,
            "BackgroundColor": "#ffffff",
            "Default": 0,
            "OnTicketCreateScreen": 0,
            "Name": "closed unsuccessful",
            "Color": "#b3b3b3",
            "Screens": {}
        },
        ...
        ],
        "Name": "State"
    }, {
        "Items": [{
            "Value": "EscalationSolutionTime",
            "Name": "By time to done"
        }, {
            "Value": "Age",
            "Name": "By creating date"
        }, {
            "Value": "Priority",
            "Name": "By priority"
        }, {
            "Value": "Changed",
            "Name": "By last update"
        }],
        "Exclusive": 1,
        "Name": "Sort"
    }],
    "Response": "OK"
}
```

#### Priority items

Color for Priority is taken from config option RS::Mobile::Priority::Color if it
is set or its DEFAULT value. Otherwise it is "#ffffff".

Default value 1 or 0 is used when Priority name as the same as Priority value
in config option Ticket::Frontend::AgentTicketPhone

#### Type items

Color and BackgroundColor are taken from RS::Mobile::Type::Color and its DEFAULT
setting when it is necesessary. Otherwise it is "#ffffff".

Abbr is taken from RS::Mobile::Type::Abbr mapping or the first three symbols of Type
names in case of lack of config option values for a Type.

#### State items

Default 1 or 0 is from RS::API::DefaultState.

IsVisible 1 or 0 if State name is in the config option Ticket::ViewableStateType
list of names.

StateType is a common class name for some types.

OnTicketCreateScreen 1 or 0 if State is a DefaultState or if State in the
restricted list of State of AgentTicketPhone page. See above for QueueID
param.

Color and BackgroundColor are taken from RS::Mobile::State::Color and its DEFAULT
setting when it is necesessary. Otherwise it is "#ffffff".

#### View items

Besides of default View items it can also return Views from Radiant System OTRS
package RS4OTRS_TicketViews.

All items of View group are predefined and hardcoded as Default one also.
