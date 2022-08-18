# Deprecated. Quoted message
> This message is deprecated and is kept for the backward compatibility. For replacement see field ```quotedMessage``` in other types of incoming messages

This section describes `messageData` object incoming webhook format for incoming quoted message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section. 

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `quotedMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`typeMessage` | **string** | Received message type. For messages of this type, the parameter takes on the value `quotedMessage`
`extendedTextMessageData` | **object** | Text message data object 

`extendedTextMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`text` | **string** | Text message below quoted 
`stanzaId` | **string** | Quoted message ID
`participant` | **string** | Recipient chat ID

### Webhook body example {#webhook-example-body}

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
