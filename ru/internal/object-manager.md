---
lang: ru
lang-ref: internal-object-manager
title: Заведующий предметами
---

Kernel::System::ObjectManager - производитель и заведующий одиночными
предметами.

Создание **заведующего** должно происходить на верхнем уровне приложения:

```perl
local $Kernel::OM = Kernel::System::ObjectManager->new();
```

Затем в любом месте можно будет обратиться к `$Kernel::OM` и получить доступ к
следующим вызовам:

- Get
- Create
- ObjectInstanceRegister
- ObjectParamAdd
- ObjectEventsHandle
- ObjectsDiscard
- ObjectRegisterEventHandler

Внутренние вызовы:

- new
- \_ObjectBuild
- \_DieWithError
- DESTROY

#### Get

Возвращает существующий, либо неявно созданный одиночный предмет.

Список созданных предметов хранится в `$Kernel::OM->{Objects}`:

Просмотреть оные можно с помощью следующего указания:

```
join("\n", keys %{ $Kernel::OM->{Objects} });
```

Неявное создание одиночного предмета происходит в `_ObjectBuild`.

#### Create

Явное создание НЕ одиночного предмета, который в последующем не управляется
данным `заведующим`. Т.е. не происходит сохранения в $Kernel::OM->{Objects}.

### ObjectInstanceRegister

Позволяет поместить существующий предмет под крыло управления заведующим. Т.е.
происходит сохранение предмета в $Kernel::OM->{Objects}.
