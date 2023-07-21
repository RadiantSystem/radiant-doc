---
lang: ru
layout: home
lang-ref: term-password
---

# Пропуск

## Расположение

Пропуск расположен в поле `pw`:

- для работников в описи `users`
- для пользователей в `customer_user`
- для письменных ящиков в `mail_account`

## Задание

- для работников с помощью вызовов `Kernel::System::User`:
  - `SetPassword()`
  - `UserAdd()`: если не указать явно, то пропуск будет создан с помощью
    `GenerateRandomPassword()` на основе `Kernel::System::Main::GenerateRandomString()`.
  - `UserUpdate()`
- для пользователей с помощью вызовов из Kernel::System::CustomerUser:
  - `SetPassword()`
  - `CustomerUserAdd()`
  - `CustomerUserUpdate()`
- для письменных ящиков с помощью вызовов Kernel::System::MailAccount:
  - `MailAccountAdd()`
  - `MailAccountUpdate()`

## Удостоверение

Смотри [Удостоверение](/ru/term/authentication)

## Проверки

- для работников: нет (необходим в `scripts/test/User.t`)
- для пользователей: `scripts/test/CustomerUser.t`
- для письменных ящиков: `scripts/test/MailAccount.t`
