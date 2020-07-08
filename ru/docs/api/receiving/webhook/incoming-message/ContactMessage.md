# Входящее сообщение с контактом

В данном разделе описываются поля webhook уведомления объекта `messageData` специфичные для входящего сообщения с контактом. Для получения описания общих полей входящих сообщений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived). 

Для получения webhook уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `contactMessage`


## Webhook {#webhook}

### Поля webhook {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `contactMessage`
`contactMessageData` | **object** | Объект данных о принятом контакте.

Поля объекта `contactMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`displayName` | **string** | Отображаемое имя контакта
`vcard` | **string** | Структура VCard (визитной карточки контакта)

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
        "typeMessage": "contactMessage",
        "contactMessageData": {
            "displayName": "Виктор Андреевич",
            "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Андреевич;Виктор;;;\nFN:Виктор Андреевич\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
        }
    }
}
```
