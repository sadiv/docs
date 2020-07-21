# Входящее текстовое сообщение с URL

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего текстового сообщение с URL. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `extendedTextMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `extendedTextMessage`
`extendedTextMessageData` | **object** | Объект данных о принятой ссылке с метаданными

Поля объекта `extendedTextMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`text` | **string** | Текст ссылки
`description` | **string** | Описание ссылки
`title` | **string** | Заголовок ссылки
`previewType` | **string** | Тип превью ссылки
`jpegThumbnail` | **string** | Превью изображения в `base64` кодировке

### Пример тела уведомления {#webhook-example-body}

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
        "typeMessage": "extendedTextMessage",
        "extendedTextMessageData": {
            "text": "https://green-api.com/docs/video",
            "description": "Green API docs shows how you can develop the WhatsApp Bot",
            "title": "How to develop WhatsApp Bot",
            "previewType": "video",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFxQYG=="
        }
    }
}
```
