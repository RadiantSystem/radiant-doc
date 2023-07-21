---
lang: ru
lang-ref: packages-api-info
title: RS4OTRS_API
---

### О расширении

RS4OTRS_API расширение для взаимодействие с ОТРС посредством JSON запросов.

### Установка

- Обычным способом установи JSON API расширение выпуска 6.41.0 или новее на
  ОТРС.

- В записе zzz_otrs.conf внутри раздела <Location /otrs> добавь:

```
RewriteEngine on
RewriteRule "/api/(\w+)/(\w+)" "/otrs/json.pl?Action=$1&Subaction=$2" [QSA,L]
```

- Перезапусти Апач.

### HTTP взаимодействие

API поддерживает GET и POST HTTP запросы, но по причине безопасности тебе
следует ограничиться только POST запросами с JSON содержимым в них
(application/json).

### Ключ доступа и разрешения

Почти все вызовы требуют ключ доступа. Его можно получить посредством вызова
/auth/login.

Без ключа доступа или с недействительным оным ты получишь ошибку:

```
{
    "Response": "ERROR",
    "Message": "Session invalid. Please log in again."
}
```

Некоторые вызовы проверяют разрешения пользователя на выполнение запрашиваемого
действия (Разрешения работников по отделам). Для таких вызовов здесь в описании
к оным присутствует поле "Необходимые разрешения" со списком разрешений по
отделам.

### Ответ с ошибкой

Помимо "Session invalid." есть и другая общая ошибка:

```
{
    "Message": "Please contact the administrator.",
    "Response": "ERROR"
}
```

для неожидаемых случаев.

### Пример запросов

POST запрос для /auth/login:

```
curl -s -X POST
  -H 'Content-Type: application/json' localhost/otrs/api/auth/login
  -d '{"User":"root@localhost", "Password": "kBHsn6"}'
```

GET запрос:

```
curl -s -X GET
"localhost/bin/api/auth/login?User=root@localhost&Password=kBHsn6"
```

### Список вызовов

#### Доступа /auth

- [/login](/ru/packages/api/methods/auth/login)
- [/logout](/ru/packages/api/methods/auth/logout)
- [/lostPassword](/ru/packages/api/methods/auth/lostPassword)

#### Пользователи /customers

- [/createCustomerUser](/ru/packages/api/methods/customers/createCustomerUser)
- [/getCustomerList](/ru/packages/api/methods/customers/getCustomerList)
- [/getCustomerUser](/ru/packages/api/methods/customers/getCustomerUser)
- [/getCustomerUserList](/ru/packages/api/methods/customers/getCustomerUserList)

#### Отсеиватели /filters

- [/getTicketViews](/ru/packages/api/methods/filters/getTicketViews)

#### Очереди /queues

- [/getQueueList](/ru/packages/api/methods/queues/getQueueList)

#### Службы /services

- [/getServiceList](/ru/packages/api/methods/services/getServiceList)

#### Настройки /settings

- [/getLanguageList](/ru/packages/api/methods/settings/getLanguageList)
- [/setPushNotificationToken](/ru/packages/api/methods/settings/setPushNotificationToken)

#### Уровни обслуживания /sla

- [/getSLAList](/ru/packages/api/methods/sla/getSLAList)

#### Служебные /system

- [/getPackageList](/ru/packages/api/methods/system/getPackageList)
- [/getDynamicFieldList](/ru/packages/api/methods/system/getDynamicFieldList)

#### Заявки /tickets

- [/createArticle](/ru/packages/api/methods/tickets/createArticle)
- [/createAttachment](/ru/packages/api/methods/tickets/createAttachment)
- [/createTicket](/ru/packages/api/methods/tickets/createTicket)
- [/getArticles](/ru/packages/api/methods/tickets/getArticles)
- [/getAttachment](/ru/packages/api/methods/tickets/getAttachment)
- [/getTicketList](/ru/packages/api/methods/tickets/getTicketList)
- [/markArticleAsSeen](/ru/packages/api/methods/tickets/markArticleAsSeen)
- [/markTicketAsSeen](/ru/packages/api/methods/tickets/markTicketAsSeen)
- [/updateArchiveFlag](/ru/packages/api/methods/tickets/updateArchiveFlag)
- [/updateCustomer](/ru/packages/api/methods/tickets/updateCustomer)
- [/updateLock](/ru/packages/api/methods/tickets/updateLock)
- [/updateOwner](/ru/packages/api/methods/tickets/updateOwner)
- [/updatePendingTime](/ru/packages/api/methods/tickets/updatePendingTime)
- [/updatePriority](/ru/packages/api/methods/tickets/updatePriority)
- [/updateQueue](/ru/packages/api/methods/tickets/updateQueue)
- [/updateResponsible](/ru/packages/api/methods/tickets/updateResponsible)
- [/updateService](/ru/packages/api/methods/tickets/updateService)
- [/updateSLA](/ru/packages/api/methods/tickets/updateSLA)
- [/updateState](/ru/packages/api/methods/tickets/updateState)
- [/updateTicket](/ru/packages/api/methods/tickets/updateTicket)
- [/updateTitle](/ru/packages/api/methods/tickets/updateTitle)
- [/updateType](/ru/packages/api/methods/tickets/updateType)
- [/watchTicket](/ru/packages/api/methods/tickets/watchTicket)

#### Работники /users

- [/getUserList](/ru/packages/api/methods/users/getUserList)
- [/getUserPermissions](/ru/packages/api/methods/users/getUserPermissions)

### Настройка приложения для Андроид/иОС

- [Уведомления](/ru/packages/api/mobile)

### Справка

- [Изменения](/ru/packages/api/changes)
