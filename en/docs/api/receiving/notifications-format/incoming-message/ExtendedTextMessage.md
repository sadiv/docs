# Incoming text message with URL

This section describes `messageData` object incoming webhook format for incoming text message with URL. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section. 

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `extendedTextMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`typeMessage` | **string** | Incoming mesage type. For messages of this type, the parameter takes on the value `extendedTextMessage`
`extendedTextMessageData` | **object** | Data object on incoming link with meta-data

`extendedTextMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`text` | **string** | Link text
`description` | **string** | Link description
`title` | **string** | Link title
`jpegThumbnail` | **string** | `base64`-coded image preview

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
        "typeMessage": "extendedTextMessage",
        "extendedTextMessageData": {
            "text": "https://green-api.com/docs/video",
            "description": "Green API docs shows how you can develop the WhatsApp Bot",
            "title": "How to develop WhatsApp Bot",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFxQYG=="
        }
    }
}
```
