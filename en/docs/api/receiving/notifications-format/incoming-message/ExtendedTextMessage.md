# Incoming text message or URL message

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
`quotedMessage` | **object** | Quoted message data object. Present only if the message itself is a quote

`extendedTextMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`text` | **string** | Link text or ordinary text
`description` | **string** | Link description, may be empty
`title` | **string** | Link title, may be empty
`jpegThumbnail` | **string** | `base64`-coded image preview, may be absent

`quotedMessage` object parameters

| Parameter     | Type       | Description                          |
| ------------- | ---------- | ------------------------------------ |
| `stanzaId`    | **string** | quoted message id                    |
| `participant` | **string** | quoted message sender's id           |
| `typeMessage` | **string** | quoted message type                  |

The rest of the fields are filled depending on the type of the quoted message and are identical to the fields of incoming messages described in [Входящие сообщения](Webhook-IncomingMessageReceived.md) section

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
            "description": "Green API docs show how you can develop the WhatsApp Bot",
            "title": "How to develop WhatsApp Bot",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFxQYG=="
        }
    }
}
```

### Link or text and contact quote incoming message webhook body example {#webhook-example-body}

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
    "typeMessage": "quotedMessage",
    "extendedTextMessageData": {
      "text": "https://yandex.ru/former&utm_source=home&utm_content=main_informer&utm_term=main_number",
      "stanzaId": "0EA554E587820E35309858AE265BE7EA",
      "participant": "79001230000@c.us"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79061230000@c.us",
      "typeMessage": "contactMessage",
      "contact": {
        "displayName": "Green-Api",
        "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Green-Api\nitem1.TEL;waid=79001230000\nitem1.X-ABLabel:Mobile\nEND:VCARD"
      }
    }
  }
}
```

###  Link and image quote incoming message webhook body example {#webhook-example-body}

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
    "typeMessage": "quotedMessage",
    "extendedTextMessageData": {
      "text": "https://yandex.ru/pogoda/?utm_medium=source=home&utm_content=main_informer&utm_term=main_number",
      "stanzaId": "B4AA239D112CB2576897B3910FEDE26E",
      "participant": "79001230000@c.us"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79061230000@c.us",
      "typeMessage": "imageMessage",
      "downloadUrl": "",
      "caption": ""
    }
  }
}
```
