---
lang: ru
lang-ref: auth-login
title: "RS4OTRS_API: auth/login"
---

### Вход

**/auth/login**

Необходимые поля:

| **Название** | **Описание** |
| User | Имя работника. |
| Password | Пропуск работника |

Успешный ответ:

```
{
    "Response": "OK",
    "Message": "Successful login",

    "SessionName": "SessionName значение из Настроек",

    # Ключ доступа
    "SessionValue": "KWhkYIZhLWOu9ptvPF1zpMYN9W4CuWQD"

    # Дополнительный ключ
    "ChallengeToken": "8TuwMme0pnTzelSEbx81yhb6gK8O076L",

    "Me": {
        "UserLogin": "root@localhost",
        "Email": "root@localhost",
        "FirstName": "Admin",
        "LastName": "OTRS",
        "FullName": "Admin OTRS",
        "ID": 1,
        "Avatar": "string"
    },
    "Settings": {
        "Language": "string"
    }
}
```

В случае:

- неуспешной попытки входа;
- отсутствия сведений о работнике;
- неудачной попытки создания взаимодействия для работника.

```
{
    "Message"  : "Login failed! Your user name or password was entered incorrectly.",
    "Response" : "ERROR"
}
```
