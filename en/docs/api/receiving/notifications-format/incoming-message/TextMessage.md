# Incoming text message 

This section describes `messageData` object incoming webhook format for incoming text message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section. 

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `textMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

Parameter | Type | Descriptionе
----- | ----- | -----
`typeMessage` | **string** | Received message type. For messages of this type, the parameter takes on the value `textMessage` 
`textMessageData` | **object** | Text message data object 

`textMessageData` object parameters

Parameter | type | Description
----- | ----- | -----
`textMessage` | **string** | Text message

### Webhook body example {#webhook-example-body}

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
