---
lang: ru
lang-ref: datetime-functions
title: Работа со временем и датами
---

При работа с датами и временем следует учитывать часовые пояса:

- устройства на котором установлен Радиант (ОС);
- БД;
- настройки пользователя.

При входе (Action=Login) в Радиант пользователю присваивается значение для поля
UserTimeZone исходя из следующих правил:

- если часовой пояс указан пользователем в личных настройках
  (Action=AgentPreferences), то он и используется в качестве ЧП для текущего
  взаимодействия с Радиант;
- в противном случае используется значение по умолчанию, заданное в настройках
  Радиант для поля UserDefaultTimeZone;
- в случае отсутствия оного используется UTC.

Соответственно всякий раз, когда потребуется преобразовать дату и время к
часовому поясу пользователя, нужно использовать значение UserTimeZone, которое
можно узнать при вызове Kernel::System::User::GetUserData.

### Возможности Kernel::System::DateTime для работы со временем и датами

Основные вызовы для работы со временем и датами расположены в
Kernel::System::DateTime.

#### Создать

- new
- Set
- Clone

#### Получить

- Get
- RadiantTimeZoneGet
- UserDefaultTimeZoneGet
- SystemTimeZoneGet
- LastDayOfMonthGet
- TimeZoneList
- TimeZoneByOffsetList

#### Изменить

- Add
- Subtract

#### Преобразовать

- Format
- ToTimeZone
- ToRadiantTimeZone
- ToEpoch
- ToString
- ToEmailTimeStamp
- ToСTimeString

#### Проверить

- Validate
- IsVacationDay
- IsTimeZoneValid

#### Сравнить

- Delta
- Compare
