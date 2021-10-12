# Incoming call

A webhook of this type appears when there is an incoming call and contains information about the initiator and recipient of the call.

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

Parameter | Type | Description
----- | ----- | -----
`from` | **string** | Call initiator [Id](../../../chat-id) 
`typeWebhook` | **string** | [Incoming webhook type](type-webhook.md). For webhooks of this type the parameter takes on the value `incomingCall`
`instanceData` | **object** | Account data
`timestamp` | **integer** | Event timestamp in UNIX format
`idMessage` | **string** | Incoming call Id


`instanceData` object parameters

Parameter | Type | Description
----- | ----- | -----
`idInstance` | **integer** | Account Id
`wid` | **string** | Account Id in WhatsApp format
`typeInstance` | **string** | Account messenger type 

### Webhook body example {#webhook-example-body}

```json
{
    "from": "79001234500@c.us",
    "typeWebhook": "incomingCall",
    "instanceData": {
        "idInstance": 1234,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
     "timestamp": 1617691757,
     "idMessage": "104179EDB7F5328988D8834107EEBE50"
}
```
