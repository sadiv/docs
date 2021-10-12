# Account status

Incoming webhook of this type contains the account authorization status data

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

Parameter | Type | Description
----- | ----- | -----
`typeWebhook` | **string** | [Incoming webhook type](type-webhook.md). For webhooks of this type the parameter takes on the value `stateInstanceChanged`
`instanceData` | **object** | Account data
`timestamp` | **integer** | Event timestamp in UNIX format
`stateInstance` | **string** | Account state. Have variants:
| | `notAuthorized` - Account not authorized. For account authorization refer to [Before you start](../../../before-start.md#qr) section
| | `authorized` - Account authorized
| | `sleepMode` - Account is in sleep mode. The state is possible when the phone is switched off. After the phone is switched on, it may take up to 5 minutes for the account state to be changed to `authorized`.

`instanceData` object parameters

Parameter | Type | Description
----- | ----- | -----
`idInstance` | **integer** | Account Id
`wid` | **string** | Account Id in WhatsApp format
`typeInstance` | **string** | Messenger type for the account

### Webhook body example {#webhook-example-body}

```json
{
    "typeWebhook":"stateInstanceChanged",
    "instanceData": {
        "idInstance": 1,
        "wid": "79001234567@c.us",
        "typeInstance":"whatsapp"
    },
    "timestamp": 1586700690,
    "stateInstance": "notAuthorized"
}
```
