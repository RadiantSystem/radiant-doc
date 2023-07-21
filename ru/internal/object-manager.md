---
lang: ru
lang-ref: internal-object-manager
title: Управляющий сущностями
---

Kernel::System::ObjectManager - производитель и заведующий одиночными
сущностями.

Создание **управляющего** должно происходить на верхнем уровне приложения:

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

Возвращает существующий, либо неявно созданную одиночную сущность.

Список созданных сущностей хранится в `$Kernel::OM->{Objects}`:

Просмотреть оные можно с помощью следующего указания:

```
join("\n", keys %{ $Kernel::OM->{Objects} });
```

Неявное создание одиночной сущности происходит в `_ObjectBuild`.

#### Create

Явное создание НЕ одиночной сущности, которая в последующем не управляется
данным `управляющим`. Т.е. не происходит сохранения в $Kernel::OM->{Objects}.

### ObjectInstanceRegister

Позволяет поместить существующий сущность под крыло управления управляющим. Т.е.
происходит сохранение сущности в $Kernel::OM->{Objects}.
