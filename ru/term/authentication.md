---
lang: ru
layout: home
lang-ref: term-authentication
---

# Удостоверение

## Посредством проверки пропуска

- для работников с помощью `Kernel::System::Auth::Auth()`

## Проверка пропуска для работников

В `Kernel::System::Auth::Auth()` происходит вызов настроенного `AuthModuleN` (N от
'' до 10) посредством вызова `Auth()` этого расширения.

В случае неудачной проверки доступа средствами AuthModuleN::Auth(), проверка
может быть продолжена посредством
[Двухшагового удостоверения](/ru/term/two-factor-authentication)
