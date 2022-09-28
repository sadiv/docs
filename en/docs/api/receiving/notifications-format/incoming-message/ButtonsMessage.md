# Incoming buttons message

This section describes `messageData` object incoming webhook format for incoming buttons message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md).

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `buttonsMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

| Parameter          | Type        | Description                                                                                     |
| ----------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Incoming message type. For messages of this type the parameter takes on the value `buttonsMessage`       |
| `buttonsMessage` | **object** | Buttons data object                                                           |
| `quotedMessage`   | **object** | Quoted message data object. Present only if the message itself is a quote |

`buttonsMessage` object parameters

| Parameter      | Type      | Description          |
| ------------- | ---------- | ------------------- |
| `contentText` | **string** | Buttons body text message|
| `footer` | **string** | Buttons footer text message|
| `buttons`   | **object** | Buttons data object |

`buttons` object parameters

| Parameter      | Type       | Description        |
| ------------- | ---------- | ------------------- |
| `buttonId` | **string** | Button id |
| `buttonText` | **string** | Button text |

`quotedMessage` object parameters

| Parameter     | Type        | Description           |
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
        "typeMessage": "buttonsMessage",
        "buttonsMessage": {
            "contentText": "Hello",
            "footer": "Hello",
            "buttons": [
                {
                    "buttonId": "1",
                    "buttonText": "green"
                },
                {
                    "buttonId": "2",
                    "buttonText": "red"
                },
                {
                    "buttonId": "3",
                    "buttonText": "blue"
                }
            ]
        }
    }
}
```
