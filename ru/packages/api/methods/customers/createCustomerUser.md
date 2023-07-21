---
lang: ru
lang-ref: customers-create-customer-user
title: "RS4OTRS_API: customers/createCustomerUser"
---

### Создать пользователя

**/customers/createCustomerUser**

Необходимые поля:

| **Название** | **Описание** |
| Значение поля "SessionName" из ответа для /auth/login | Ключ доступа. |
| Firstname | Имя. |
| Lastname | Родность. |
| CustomerID | CustomerID. |
| Login | Имя. |
| Email | Ящик. |

Необязательные поля:

| **Название** | **Описание** |
| Password | Пропуск. |
| Country | Страна. |
| City | Город. |
| Street | Улица. |
| Zip | |
| Phone | |
| Mobile | |
| Fax | |
| Title | |
| Comment | |
| InterfaceLanguage | ru, en и т.п. |

Успешный ответ:

```
{ "Response": "OK" }
```

Без необходимых полей:

```
{
    "Message": "Required fields is not defined: Firstname, Lastname, CustomerID, Login, Email",
    "Response": "ERROR"
}
```

Не может создать пользователя:

```
{
    "Response": "ERROR",
    "Message": "Couldn't create customer user"
}
```
