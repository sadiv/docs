# Account socket status

This type webhook contains socket state data (whether instance is ready to send/receive messages)

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

Parameter | Type | Description
----- | ----- | -----
`typeWebhook` | **string** | [Webhook type](type-webhook.md). For this type notifications the parameter takes on value `statusInstanceChanged`
`instanceData` | **object** | Account data
`timestamp` | **integer** | Event timestamp in UNIX format
`statusInstance` | **string** | Account status. Takes on values:
| | `online` - Account can receive/send messages, socket is open
| | `offline` - Account can't receive/send messages, socet is closed

`instanceData` object parameter

Parameter | Type | Description
----- | ----- | -----
`idInstance` | **integer** | Account Id
`wid` | **string** | Account Id in WhatsApp format
`typeInstance` | **string** | Messenger type for account

### Webhook body example {#webhook-example-body}

```json
{
    "typeWebhook":"statusInstanceChanged",
    "instanceData": {
        "idInstance": 1,
        "wid": "79001234567@c.us",
        "typeInstance":"whatsapp"
    },
    "timestamp": 1586700690,
    "statusInstance": "online"
}
```
