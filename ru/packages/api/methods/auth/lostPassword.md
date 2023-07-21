---
lang: ru
lang-ref: auth-lost-password
title: "RS4OTRS_API: auth/lostPassword"
---

### Сбросить пропуск

**/auth/lostPassword**

Необходимые поля:

| **Название** | **Описание** |
| User | Имя работника. |
| Token | Ключ из письма, когда щёлкаем по ссылке "Забыл пропуск" на странице входа в ОТРС. |

Успешный ответ. Для случаев действительных и недействительных (несуществующих)
работнико по причине безопасности:

```
{
    "Message": "Sent password reset instructions. Please check your email.",
    "Response" : "OK"
}
```

В случае щелчка по ссылке из письма:

```
{
    "Message": "Sent new password to 'UserName'. Please check your email.",
    "Response" : "OK"
}
```

В случае отключенной возможности сбрасывать пропуск:

```
{
    "Message": "Feature not active.",
    "Response": "ERROR"
}
```

В случае ошибки при отправке письма с руководством или с новым пропуском:

```
{
    "Message": "Please contact the administrator.",
    "Response": "ERROR"
}
```

В случае недействительного ключа, когда работник сбрасывает пропуск посредством
ссылки из письма:

```
{
    "Message": "Invalid token.",
    "Response": "ERROR"
}
```
