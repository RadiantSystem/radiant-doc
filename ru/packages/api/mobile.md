---
lang: ru
lang-ref: packages-api-mobile
title: RS4OTRS_API
---

## Mobile notifications

### Preparation

It doesn't work without the package "RS4OTRS\_Mobile" for notifications!

At first you should get Server key in Project list here:
[https://console.firebase.google.com](https://console.firebase.google.com),
[https://firebase.google.com/docs/cloud-messaging/auth-server](https://firebase.google.com/docs/cloud-messaging/auth-server)

Then in the file PushNotify.yml add it as additional header:

```
Headers:
  Authorization: "key=AIzaSyAAz4rPdvewnTId2Xj7k83VLXpAUM"
```

Create Webservice by importing PushNotify.yml.

On the Ticket Notification Management page:
https://yourotrsdomain.com/otrs/index.pl?Action=AdminNotificationEvent.

Set appropriate notifications and turn on "Push notification" flag.

All messages will be sent to mobile phones from this point.

Request to Google looks like this:

```
curl https://fcm.googleapis.com/fcm/send
-H "Authorization:key=AIzaSyAAz4rOeb2gPdvewn"
-H "Content-Type: application/json"
-X POST
-d '{
  "data" : {
    "detail" : "Privet",
    "server" : "yourotrsdomain.com",
    "ticket_id" : "1840",
    "title" : "[Ticket#2019010948000063] Ticket Note: Zdravstvuite"
  },
  "to" : "cEyZA21_jBA:APA91bH6Uf2SFvK0eyzCx"
}'
```

And response:

```
{
  "multicast_id":709155803348687313,
  "success":1,
  "failure":0,
  "canonical_ids":0,
  "results":[
      {"message_id":"0:1547053856660693%53302b409fd7ecd"}
  ]
}
```
