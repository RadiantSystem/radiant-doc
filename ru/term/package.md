---
lang: ru
layout: home
lang-ref: term-package
---

# Расширение

## Выполнение дополнительных указаний при установке, переустановке, удалении или обновлении

Задают в соответствующих разделах .opm сборки:

- CodeInstall
- CodeReinstall
- CodeUninstall
- CodeUpgrade

Они могут быть расположены там целиком, либо лишь соответствующие вызовы на
указания, расположенные в отдельной .pm записи, которую располагают как правило
по следующему пути: `var/packagesetup/*.pm`

Пример подобного вызова:

```xml
<CodeInstall Type="post"><![CDATA[
    my $CodeModule = 'var::packagesetup::' . $Param{Structure}->{Name}->{Content};

    $Kernel::OM->Get($CodeModule)->CodeInstall();
]]></CodeInstall>
```

В данном случае происходит вызов `CodeInstall()` после (`Type="post"`) того как
расширение будет добавлено на площадку. Это возможно за счёт того, что внутри
раздела `CodeInstall` видна переменная `$Param{Structure}` с содержимым
расширения, благодяря которой можно узнать имя задействованного расширения и по
нему вычислить путь к .pm, расположенном в `var/packagesetup/*.pm`.

Непосредственно вызовы CodeInstall, CodeReinstall, CodeUninstall, CodeUpgrade
происходят в `Kernel::System::Package` внутри:

- PackageInstall()
- PackageReinstall()
- PackageUninstall()
- PackageUpgrade()

## Распространённые действия, выполняемые при обработке расширения

- Измененение изменяемых полей: создание, удаление и т.п.
- Изменение состава описей:
  - Создание описи
  - Удаление описи
  - Изменение описи
- Изменение содержимого описей:
  - Создание записи
  - Удаление записи
  - Изменение записи
