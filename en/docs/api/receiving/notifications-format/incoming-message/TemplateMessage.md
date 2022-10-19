# Template buttons incoming message

This section describes `messageData` object incoming webhook format for buttons incoming template message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section.

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `templateMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

| Parameter           | Type        | Description                                                                                          |
| ----------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Incoming message type. For messages of this type the parameter takes on the value `templateMessage`       |
| `templateMessage` | **object** | Buttons data object                                                           |
| `quotedMessage`   | **object** | Quoted message data object. Present only if the message itself is a quote |

`templateMessage` object parameters

| Parameter      | Type        | Description               |
| ------------- | ---------- | ------------------- |
| `contentText` | **string** | Buttons body text message|
| `footer` | **string** | Buttons footer text message|
| `buttons`   | **object** | Buttons data object |

`buttons` object parameters

| Parameter       | Type       | Description               |
| ------------- | ---------- | ------------------- |
| `index` | **string** | Button index |
| `urlButton` | **object** | Url button data object |
| `callButton` | **object** | Callback button data object |
| `quickReplyButton` | **object** | Quick reply button data object |

`urlButton` object parameters

| Parameter       | Type       | Description       |
| ------------- | ---------- | ------------------- |
| `displayText` | **string** | Button url text|
| `url` | **string** | Link |

`callButton` object parameters

| Parameter        | Type      | Description          |
| ------------- | ---------- | ------------------- |
| `displayText` | **string** | Callback button text|
| `phoneNumber` | **string** | Telephone number |

`quickReplyButton` object parameters

| Parameter      | Type       | Description          |
| ------------- | ---------- | ------------------- |
| `displayText` | **string** | Quick reply button text|
| `id` | **string** | Quick reply button id |

`quotedMessage` object parameters

| Parameter      | Type       | Description          |
| ------------- | ---------- | ------------------- |
| `stanzaId` | **string** | Quoted message id |
| `participant` | **string** | Quoted message sender's id |
| `typeMessage` | **string** | Quoted message type |

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
        "typeMessage": "templateMessage",
        "templateMessage": {
            "contentText": "Hello",
            "footer": "Hello",
            "buttons": [
                {
                    "urlButton": {
                        "displayText": "⭐ Star us on GitHub!",
                        "url": "https://github.com/green-api/docs"
                    },
                    "index": 1
                },
                {
                    "callButton": {
                        "displayText": "Call us",
                        "phoneNumber": "+1 (234) 5678-901"
                    },
                    "index": 2
                },
                {
                    "quickReplyButton": {
                        "displayText": "Hello",
                        "id": "plainButtonId"
                    },
                    "index": 3
                }
            ]
        }
    }
}
```
