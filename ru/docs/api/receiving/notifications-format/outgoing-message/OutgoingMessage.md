# Отправленное с телефона сообщение

Формат сообщения, отправленного с телефона идентично формату [входящего сообщения](../incoming-message/Webhook-IncomingMessageReceived.md), при этом [тип входящего уведомления](../type-webhook.md) принимает значение `outgoingMessageReceived`.

### Пример тела уведомления {#webhook-example-body}

```json
{
    "typeWebhook": "outgoingMessageReceived",
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
       // В зависимости от typeMessage = textMessage || imageMessage || videoMessage || documentMessage || audioMessage || locationMessage || contactMessage || extendedTextMessage
       ...
       ...
       ...
        }
    }
}
```