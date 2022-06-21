# Before you start

Before you start working with Green API you are required to follow the below steps:

1. [Create Account in Your profile](#cabinet)
2. [Create User account](#account)
3. [Install mobile app WhatsApp Business](#mobile)
4. [Authorize User account](#qr)
5. [Get access parameters to User account](#parameters)
6. [Set receiving incoming data](#receiving)

## 1. Create account in Your profile {#cabinet}

To create Account go to [Your profile](https://console.green-api.com). After authorization in your profile, you will be able to create a user account. In your profile you may create several user accounts for one account. 

## 2. Create  User account {#account}

User account is created in your profile and is used to organize HTTP API WhatsApp. One user account may serve only one phone number at a time (one WhatApp account). When creating a user account you are to select a tariff. 

## 3. Install mobile app WhatsApp Business {#mobile}

Sending and receiving WhatsApp messages is done from your mobile phone. The phone must have the official [WhatsApp Business](https://www.whatsapp.com/business/) mobile app installed. It is also allowed to use the mobile application [WhatsApp](https://www.whatsapp.com/), if the use of [WhatsApp Business](https://www.whatsapp.com/business/) is impossible for any reason.

> It is recommended to order **Handset hosting** service. In this case, a personal mobile phone is not required. Sending and receiving WhatsApp messages will be carried out from a mobile phone located in the Green API data center. 

## 4. Authorize User account {#qr}

If you use a personal mobile phone for work with Green API, you have to authorize User account. Account authorization is carried out in [Your profile](https://console.green-api.com) by scanning QR code from [WhatsApp Business](https://www.whatsapp.com/business/) mobile app. To do this, open [WhatsApp Business](https://www.whatsapp.com/business/) application on your mobile phone, go to the application settings and scan the QR code displayed in your profile.

- Android: `WhatsApp Business` -> `Drop down menu` -> `WhatsApp Web`
- iPhone: `WhatsApp Business` -> `Settings` -> `WhatsApp Web` -> `Scan QR code`

> Sending and receiving messages are carried out from your mobile phone. Therefore, the phone has to be always charged and connected to the Internet.

## 5. Get access parameters to User account {#parameters}

To execute HTTP API WhatsApp requests, you need to use the access parameters to User account. Access parameters are published in [Your profile](https://console.green-api.com):

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

Account access key can be changed if necessary, for example, if it is compomised.

## 6. Set receiving incoming data {#receiving}

If you need to receive incoming data (incoming messages, previously sent messages statuses, etc.), then you have first to make [account setup](api/receiving/index.md). You can get incoming webhooks via [HTTP API](api/receiving/technology-http-api.md) or [Webhook Endpoint](api/receiving/technology-webhook-endpoint.md).

## Done!

Everything is ready to start sending and receiving WhatsApp messages! 

To debug requests to the Green API, it is recommended to use [Postman collection](postman-collection.md)
