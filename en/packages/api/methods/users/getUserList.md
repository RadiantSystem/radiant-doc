---
lang: en
lang-ref: users-get-user-list
title: "RS4OTRS_API: users/getUserList"
---

## Get user list

**/users/getUserList**

Required parameters:

- The value of "SessionName" field of /auth/login response - main token

Unrequired parameters:

- QueueID - queue id.

Successful answer:

```
{
    "Users": [{
        "AdminCommunicationLogPageShown": 25,
        "AdminDynamicFieldsOverviewPageShown": 25,
        "ChangeTime": "2018-02-27 09:05:43",
        "CreateTime": "2018-02-27 09:05:43",
        "UserAuthBackend": null,
        "UserChangeOverviewSmallPageShown": 25,
        "UserConfigItemOverviewSmallPageShown": 25,
        "UserCreateNextMask": null,
        "UserEmail": "root@localhost",
        "UserFAQJournalOverviewSmallPageShown": 25,
        "UserFAQOverviewSmallPageShown": 25,
        "UserFirstname": "Admin",
        "UserFullname": "Admin OTRS",
        "UserID": 1,
        "UserLanguage": "ru",
        "UserLastLogin": 1567423376,
        "UserLastLoginTimestamp": "2019-09-02 11:22:56",
        "UserLastname": "OTRS",
        "UserLogin": "root@localhost",
        "UserLoginFailed": 0,
        "UserPw": "9334e4ad11f971db5b922cab",
        "UserRefreshTime": 0,
        "UserStoredFilterColumns-AgentTicketEscalationView": "{}",
        "UserStoredFilterColumns-AgentTicketStatusView": "{}",
        "UserSurveyOverviewSmallPageShown": 25,
        "UserSystemConfigurationCategory": null,
        "UserTicketOverviewAgentCustomerSearch": "Small",
        "UserTicketOverviewAgentTicketEscalationView": "Small",
        "UserTicketOverviewAgentTicketStatusView": "Small",
        "UserTicketOverviewMediumPageShown": 20,
        "UserTicketOverviewPreviewPageShown": 15,
        "UserTicketOverviewSmallPageShown": 25,
        "UserTimeZone": "Europe/Moscow"
        "UserTitle": null,
        "ValidID": 1,
    }],
    "Count": 1,
    "Response": "OK"
}
```
