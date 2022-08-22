# Sent message via API

The format of a message, sent via API, is the same as for an [incoming message](../incoming-message/Webhook-IncomingMessageReceived.md), and [Incoming webhooks type(../type-webhook.md) takes on the value `outgoingAPIMessageReceived`.

### Webhook body example {#webhook-example-body}

```json
{
    "typeWebhook": "outgoingAPIMessageReceived",
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
       // Depending on typeMessage = textMessage || imageMessage || videoMessage || documentMessage || audioMessage || locationMessage || contactMessage || extendedTextMessage
       ...
       ...
       ...
        }
    }
}
```
