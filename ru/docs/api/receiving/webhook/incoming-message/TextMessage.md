# Webhook IncomingMessageReceived TextMessage

Входящее текстовое сообщение.

## Webhook {#webhook}

### Поля webhook {#webhook-parameters}

В данном разделе описываются поля webhook уведомления объекта `messageData` специфичные для входящего текстового сообщения. Для получения описания общих полей входящих сообщений обратитесь к разделу [Входящие сообщения](/api/receiving/webhook/incoming-message/Webhook-IncomingMessageReceived). 

Для получения webhook уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `textMessage`


Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `textMessage`
`textMessageData` | **object** | Объект данных о текстовом сообщении

Поля объекта `textMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`textMessage` | **string** | Текстовое сообщение

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
    "messageData":{
        "typeMessage":"textMessage",
        "textMessageData":{
            "textMessage":"I use Green-API to send this message to you!"
        }
    }
}
```
