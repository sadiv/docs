# List element selection


This section describes `messageData` object incoming webhook format for selection list. For a description of the general format of incoming webhooks, refer to [Incoming messages](/../docs/api/receiving/notifications-format/) section. 

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`typeMessage` | **string** | Received message type. For messages of this type, the parameter takes on the value `listResponseMessage`
`listResponseMessage` | **object** | Data object on the user's selection of a list value
`quotedMessage` | **object** | Quoted message data object. Present only if the message itself is a quote

`listResponseMessage` object parameters

Parameter | Type | Description
----- | ----- | -----
`title` | **string** | selected value text
`listType` | **string** | list type. 1 - single value selection
`singleSelectReply` | **string** | selected value id
`stanzaId` | **string** | button message ID


### Webhook body example {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1101000001,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1657025112,
    "idMessage": "A36C68A09C54796295FCAD20C15C534C",
    "senderData": {
        "chatId": "79001234567@c.us",
        "sender": "79001234567@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "listResponseMessage",
        "listResponseMessage": {
            "stanzaId": "BAE53AFDD5F0C137",
            "title": "Option 2",
            "listType": 1,
            "singleSelectReply": "option2"
        }
    }
}
```
