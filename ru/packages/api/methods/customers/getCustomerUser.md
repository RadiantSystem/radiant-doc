---
lang: ru
lang-ref: customers-get-customer-user
title: "RS4OTRS_API: customers/getCustomerUser"
---

### Получить пользователя

**/customers/getCustomerUser**

Необходимые поля:

| **Название** | **Описание** |
| Значение поля "SessionName" из ответа для /auth/login | Ключ доступа. |
| CustomerUser | Имя пользователя. |

Успешный ответ:

```
{
    "ValidID": 1,
    "UserEmail": "cl@rs.ngi",
    "UserComment": "",
    "UserCustomerID": "RS",
    "UserFirstname": "Ivan",
    "UserFax": "",
    "UserTitle": "RS",
    "UserLastname": "Testoviy",
    "UserZip": "",
    "UserStreet": "",
    "UserLogin": "client\_001",
    "Response": "OK",
    "UserPhone": "",
    "UserMobile": "",
    "UserCity": "",
    "UserCountry": "",
    ...
    "DynamicField_ABC": "FFF"  # настраивать в Config.pm в разделе CustomerUser Map
}
```

Нет поля CustomerUser:

```
{
    "Response": "ERROR",
    "Message": "No CustomerUser parameter"
}
```

Нет CustomerUser:

```
{
    "Response": "ERROR",
    "Message": "No CustomerUser"
}
```
