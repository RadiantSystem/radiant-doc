---
lang: ru
lang-ref: customers-get-customer-list
title: "RS4OTRS_API: customers/getCustomerList"
---

### Получить список пользователей

**/customers/getCustomerList**

Необходимые поля:

| **Название** | **Описание** |
| Значение поля "SessionName" из ответа для /auth/login | Ключ доступа. |

Успешный ответ:

```
{
    "CustomerCompanies": [{
        "CustomerID": "ABC",
        "Name": "ABC Company"
    }, {
        "CustomerID": "RS",
        "Name": "RS Company"
    }],
    "Response": "OK"
}
```
