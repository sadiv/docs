# Template button selection

This section describes `messageData` object incoming webhook format for template buttons. For a description of the general format of incoming webhooks, refer to [Incoming messages](/../docs/api/receiving/notifications-format/) section. 

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData`object parameters

Parameter | Type | Description
----- | ----- | -----
`typeMessage` | **string** | Received message type. For messages of this type, the parameter takes on the value `templateButtonsReplyMessage`
`templateButtonReplyMessage` | **object** | Data object on the user's button selection

`templateButtonReplyMessage` object parameters

Parameter | Type | Description
----- | ----- | -----
`selectedIndex` | **string** | selected button digital index
`selectedId` | **string** | selected button identifier
`selectedDisplayText` | **string** | selected button text
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
    "timestamp": 1656315272,
    "idMessage": "9BB19BB0D568BA7B185EEAD21A33D317",
    "senderData": {
        "chatId": "79001234567@c.us",
        "sender": "79001234567@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "templateButtonReplyMessage",
        "templateButtonReplyMessage": {
            "stanzaId": "BAE53AFDD5F0C137",
            "selectedIndex": 2,
            "selectedId": "id1",
            "selectedDisplayText": "red"
        },
    }
}
```
