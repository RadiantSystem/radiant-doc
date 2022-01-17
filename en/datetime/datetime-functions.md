---
lang: en
lang-ref: datetime-functions
title: Datetime operations
---

For datetime operations it should take into account time zones:

- server on which Radiant installed (OS);
- DB;
- user settings.

When it logins (Action=Login) to Radiant a user is attached a value of
UserTimeZone based on the next rules:

- if TimeZone is set by a user in private settings (Action=AgentPreferences),
  then it is used as TZ for current Radiant session;
- otherwise by default it is used a value from Radiant settings for
  UserDefaultTimeZone field;
- if it is missed then UTC.

Accordingly every time when it is necessary to transform datetime to TZ
of a user it should be used a UserTimeZone value, which can be got from
Kernel::System::User::GetUserData call.

### Kernel::System::DateTime features for datetime operations

The main calls for datetime operations is located in Kernel::System::DateTime.

#### Create

- new
- Set
- Clone

#### Get

- Get
- RadiantTimeZoneGet
- UserDefaultTimeZoneGet
- SystemTimeZoneGet
- LastDayOfMonthGet
- TimeZoneList
- TimeZoneByOffsetList

#### Modify

- Add
- Subtract

#### Format

- Format
- ToTimeZone
- ToRadiantTimeZone
- ToEpoch
- ToString
- ToEmailTimeStamp
- ToСTimeString

#### Check

- Validate
- IsVacationDay
- IsTimeZoneValid

#### Compare

- Delta
- Compare
