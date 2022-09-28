# Selection list incoming message

This section describes `messageData` object incoming webhook format for selection list incoming message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section.

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `listMessage`

## Webkhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

| Parameter| Type | Description  |
| ----------------- | ---------- | ------------ |
| `typeMessage`     | **string** | Incoming message type. For messages of this type the parameter takes on the value `listMessage`       |
| `listMessage` | **object** | List data object |
| `quotedMessage`   | **object** | Quoted message data object. Present only if the message itself is a quote |

`listMessage` data object

| Parameter      | Type        | Description          |
| ------------- | ---------- | ------------------- |
| `contentText` | **string** | Buttons body text message|
|`title` | **string** | No | Message title|
| `footer` | **string** | Buttons footer text message|
| `listMessage` | **object** | Buttons data object |
|`buttonText` | **string** | No | selection list button text|
|`sections` | **array** | Yes | selection list values|

`sections` array parameters

| Parameter | Type       | Description              |
| -------- | ---------- | ----------------------- |
| `title`  | **string** | Selection list title |
| `rows`   | **array**  | Selection list values  |

`rows` array parameters

|Parameter | Type       | Description                     |
| -------- | ---------- | ----------------------------- |
| `title`  | **string** | list value text         |
| `rowId`  | **string** | list value identifier |
| `description` | **string** | list value description |

`quotedMessage` object parameters

| Parameter     | Type       | Description             |
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
        "typeMessage": "listMessage",
        "listMessage": {
            "contentText": "Hello",
            "title": "title",
            "footer": "Hello",
            "buttonText": "Action list",
            "sections": [
                {
                    "title": "Section 1",
                    "rows": [
                        {
                            "title": "Option 1",
                            "rowId": "option1"
                        },
                        {
                            "title": "Option 2",
                            "rowId": "option2",
                            "description": "Clarification"
                        }
                    ]
                },
                {
                    "title": "Section 2",
                    "rows": [
                        {
                            "title": "Option 3",
                            "rowId": "option3"
                        },
                        {
                            "title": "Option 4",
                            "rowId": "option4",
                            "description": "Clarification"
                }
            ]
        }
    }
}
```
