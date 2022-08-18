# Incoming contact message

This section describes `messageData` object incoming webhook format for incoming contact message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section. 

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `contactMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

| Parameter             | Type        | Description                                                                                       |
| -------------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`        | **string** | Incoming message type. For messages of this type the parameter takes on the value `contactMessage`    |
| `contactMessageData` | **object** | Incoming contact data object.                                                              |
| `quotedMessage`      | **object** | Quoted message data object. Present only if the message itself is a quote |Parameter | Type | Description

`contactMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`displayName` | **string** | Displayed contact name
`vcard` | **string** | VCard structure (contact visit card)

`quotedMessage` object parameters

| Parameter      | Type        | Description                             |
| ------------- | ---------- | ------------------------------------ |
| `stanzaId`    | **string** | quoted message id             |
| `participant` | **string** | qouted message sender's id |
| `typeMessage` | **string** | quoted message type            |

The rest of the fields are filled depending on the type of the quoted message and are identical to the fields of incoming messages described in [Incoming messages](Webhook-IncomingMessageReceived.md) section

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

### Contact and text message quote incoming message webhook body example {#webhook-example-body}

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
      "displayName": "Anti-spam",
      "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:;Anti-spam;;;\nFN:Anti-spam\nitem1.TEL:*9035936232#\nitem1.X-ABLabel:Mobile\nEND:VCARD"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79001235696@c.us",
      "typeMessage": "textMessage",
      "textMessage": "Hello"
    }
  }
}
```

### Contact and audio/video/document quote incoming message webhook body example {#webhook-example-body}

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
          "displayName": "Anti-spam",
          "vcard": "BEGIN:VCARD\nVERSION:3.0\nFN:2 Lena\nitem1.TEL;waid=79001230000\nitem1.X-ABLabel:Mobile\nEND:VCARD"
    },
    },
    "quotedMessage": {
         "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
         "participant": "79061230000@c.us",
         "typeMessage": "imageMessage",
         "downloadUrl": "",
          "caption": ""
    }
  }
```

### Contact and contact quote incoming message webhook body example {#webhook-example-body}

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
      "displayName": "",
      "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Fond;\nitem1.TEL;waid=79001203030:/em1.X-ABLabel:New type\nEND:VCARD"
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
### Contact and location quote incoming message webhook body example {#webhook-example-body}

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
      "displayName": "Fond",
      "vcard": "BEGIN:VCARD\nVERSION:3.0\nFN:2 Hearts\nitem1.TEL;waid=79200000102\nitem1.X-ABLabel:New type\nEND:VCARD"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79060002233@c.us",
      "typeMessage": "locationMessage",
      "location": {
        "nameLocation": "",
        "address": "",
        "jpegThumbnail": "",
        "latitude": 72.5922702,
        "longitude": 45.6645388
      }
    }
  }
}
```
