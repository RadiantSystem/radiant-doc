---
lang: ru
lang-ref: auth-logout
title: "RS4OTRS_API: auth/logout"
---

### Logout

**/auth/logout**

Необходимые поля:

| **Название** | **Описание** |
| Значение поля "SessionName" из ответа для /auth/login | Ключ доступа. |
| ChallengeToken | Дополнительный ключ. |

Успешный ответ:

```
{
    "Message": "Logout successful.",
    "Response": "OK"
}
```

Неуспешный ответ. В случае недействительного ChallengeToken:

```
{
    "Response": "ERROR",
    "Message": "Invalid Challenge Token!"
}
```

В случае ошибки при удалении взаимодействия:

```
{
    "Response": "ERROR",
    "Message": "Can`t remove SessionID."
}
```
