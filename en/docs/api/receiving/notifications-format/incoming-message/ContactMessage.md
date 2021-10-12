# Incoming contact message

This section describes `messageData` object incoming webhook format for incoming contact message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section. 

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `contactMessage`


## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`typeMessage` | **string** | Incoming message type. For messages of this type the parameter takes on the value `contactMessage`
`contactMessageData` | **object** | Incoming contact data object.

`contactMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`displayName` | **string** | Displayed contact name
`vcard` | **string** | VCard structure (contact visit card)

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
    "messageData": {
        "typeMessage": "contactMessage",
        "contactMessageData": {
            "displayName": "Victor Andreevich",
            "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
        }
    }
}
```
