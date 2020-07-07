# Входящее сообщение с геолокацией

В данном разделе описываются поля webhook уведомления объекта `messageData` специфичные для входящего сообщение с геолокацией. Для получения описания общих полей входящих сообщений обратитесь к разделу [Входящие сообщения](/api/receiving/webhook/incoming-message/Webhook-IncomingMessageReceived). 

Для получения webhook уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `locationMessage`

## Webhook {#webhook}

### Поля webhook {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `locationMessage`
`locationMessageData` | **object** | Объект данных о принятой геолокации

Поля объекта `locationMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`latitude` | **double** | Широта локации
`longitude` | **double** | Долгота локации
`jpegThumbnail` | **string** | Превью изображения в `base64` кодировке

### Пример тела webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "79001234568@c.us",
        "sender": "79001234568@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "locationMessage",
        "locationMessageData": {
            "latitude": 12.345678910111213,
            "longitude": 14.151617181920212,
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFx="
        }
    }
}
```
