---
lang: ru
lang-ref: packages-mobile-info
title: RS4OTRS_Mobile
---

### About

Additional settings for the mobile application Service and help desk for
OTRS 6 Community Edition.

### Key features

- Push notifications for android, ios.
- Setting styles for priority and ticket states.

### Installation

- Before installation the package, set the correct rights with the script
  `/opt/otrs/bin/otrs.SetPermissions.pl`.
- Install the Mobile package
- Check that the AndroidNotification web service has been created in
  the "OTRS/Administration/Web Services Management" section.
- Set the "Push Notification" checkboxes in notifications that should be sent
  to devices in the "OTRS/Administration/Ticket Notification Management" section.

### Usage

When authenticate in the mobile application, you can specify the full link
to otrs or the domain name only: https://ServerAddress.com/otrs/index.pl or ServerAddress.com

Possible errors when connecting a mobile application to the server:

- Error 404 - otrs configuration error
- Login failed - problem with agent login and password

### Configuration

- RS::Mobile::Type::Abbr - ticket type abbreviations.
- RS::Mobile::Priority::Color - color of the priority icon.
- RS::Mobile::State::Color - State font color.
- RS::Mobile::State::BackgroundColor - State background color.
- RS::Mobile::Type::Color - Type font color.
- RS::Mobile::Type::BackgroundColor - Type background color.

### StateType for Mobile screens for showing/editing

- Ticket::Frontend::AgentMobileEditTicket###StateType
- Ticket::Frontend::AgentMobileNewTicket###StateType
- Ticket::Frontend::AgentMobileTicketClose###StateType
- Ticket::Frontend::AgentMobileTicketNote###StateType
- Ticket::Frontend::AgentMobileTicketStatus###StateType
