# Incoming image, video, audio, document message

This section describes `messageData` object incoming webhook format for incoming image, video, audio or document message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section. 

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `imageMessage` || `videoMessage` || `documentMessage` || `audioMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`typeMessage` | **string** | Received message type. For messages of this type, the parameter takes on the value: `imageMessage`, `videoMessage`, `documentMessage`, `audioMessage`
`fileMessageData ` | **object** | Received file data object

`fileMessageData` object parameters 

Parameter | Type | Description
----- | ----- | -----
`downloadUrl` | **string** | Link to download file
`caption` | **string** | File caption

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
    "messageData":{
        "typeMessage":"imageMessage",
        "fileMessageData":{
            "downloadUrl":"https://api.green-api.com/waInstance1234/downloadFile/19136A974392FA8CF584D70DD0E1AEDF",
            "caption":"Image"
        }
    }
}
```
