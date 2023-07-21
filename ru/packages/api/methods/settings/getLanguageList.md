---
lang: ru
lang-ref: settings-get-language-list
title: "RS4OTRS_API: settings/getLanguageList"
---

### Get language list

**/settings/getLanguageList**

Return list of languages of the System. It is got from
"DefaultUsedLanguages" and "DefaultUsedLanguagesNative" system configuration.

Required parameters:

- The value of "SessionName" field of /auth/login response - main token.

Successful answer:

```
{
    "Languages": [{
        "ID": "hi",
        "Name": "Hindi"
    }, {
        "ID": "es",
        "Name": "Spanish"
    },
    ...
    ],
    "Response": "OK"
}
```
