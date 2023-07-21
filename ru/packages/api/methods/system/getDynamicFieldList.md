---
lang: ru
lang-ref: system-dynamic-field-list
title: "RS4OTRS_API: system/getDynamicFieldList"
---

### Get dynamic fields list

**/system/getDynamicFieldList**

Get information about all dynamic fields in a system.

Required parameters:

- The value of "SessionName" field of /auth/login response - main token

```
{
  "DynamicFields": {
    "Article": [
      {
        "ID": 82,
        "Screens": {},
        "FieldType": "Text",
        "Config": {},
        "Label": "MacrosId",
        "Name": "MacrosId",
        "ObjectType": "Article"
      }
    ],
    "Ticket": [
      {
        "ID": 69,
        "Screens": {},
        "FieldType": "Dropdown",
        "Config": {
          "PossibleValues": {
            "one": "Один",
            "two": "Два"
          }
        },
        "Label": "Пример",
        "Name": "Example",
        "ObjectType": "Ticket"
      },
    ],
    ...
  },
  "Response": "OK"
}
```

RS:API::Ticket::MobileScreen::DynamicFields -- is used for setting which
DynamicFields will be shown and editable on mobile application screens.
