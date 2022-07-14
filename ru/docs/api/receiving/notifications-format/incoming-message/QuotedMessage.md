# Входящее сообщение с цитатой (УСТАРЕВШЕЕ)

* Данное сообщение устарело и оставлено для обратной совместимости. Для замены смотрите поле ```quotedMessage``` в других типах входящих сообщений

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения с цитатой. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `quotedMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `quotedMessage`
`extendedTextMessageData` | **object** | Объект данных о текстовом сообщении

Поля объекта `extendedTextMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`text` | **string** | Текстовое сообщение под цитируемым
`stanzaId` | **string** | ID цитируемого сообщения
`participant` | **string** | ID чата получателя

### Пример тела уведомления {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "70009876543@c.us",
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
        "typeMessage": "quotedMessage",
        "extendedTextMessageData": {
            "text": "Цитируем это",
            "stanzaId": "3EB0D7D028C312EB513C",
            "participant": "70009876543@c.us"
        }
    }
}
```
