# Incoming location message

This section describes `messageData` object incoming webhook format for incoming location message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section. 

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `locationMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`typeMessage` | **string** | Received message type. For messages of this type, the parameter takes on the value `locationMessage`
`locationMessageData` | **object** | Received location data object
| `quotedMessage`       | **object** | Quoted message data object. Present only if the message itself is a quote |

`locationMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`latitude` | **double** | Location latitude
`longitude` | **double** | Location longitude
`jpegThumbnail` | **string** | `base64`-coded image preview

`quotedMessage` object parameters

| Parameter     | Type        | Description                             |
| ------------- | ---------- | ------------------------------------ |
| `stanzaId`    | **string** | Quoted message id             |
| `participant` | **string** | Quoted message sender's id |
| `typeMessage` | **string** | Quoted message type            |

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
    "typeMessage": "locationMessage",
    "locationMessageData": {
      "latitude": 12.345678910111213,
      "longitude": 14.151617181920212,
      "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFx="
    }
  }
}
```

### Location and text quote incoming message webhook body example {#webhook-example-body}

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
    "typeMessage": "locationMessage",
    "locationMessageData": {
      "nameLocation": "",
      "address": "",
      "jpegThumbnail": "217",
      "latitude": 74.5922641,
      "longitude": 59.6645355
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79001230022@c.us",
      "typeMessage": "textMessage",
      "textMessage": "Hello"
    }
  }
}
```
