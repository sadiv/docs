# Device status

Incoming webhook of this type contains data on battery level and the device running [WhatsApp Business](https://www.whatsapp.com/business/) application

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

Parameter | Type | Description
----- | ----- | -----
`typeWebhook` | **string** | [Incoming webhook type](type-webhook.md). For webhooks of this type the parameter takes on the value `deviceInfo`
`instanceData` | **object** | Account data
`timestamp` | **integer** | Event timestamp in UNIX format
`deviceData` | **object** | Device data

`instanceData` object parameters

Parameter | Type | Description
----- | ----- | -----
`idInstance` | **integer** | Account Id
`wid` | **string** | Account Id in WhatsApp format
`typeInstance` | **string** | Account messenger type

`deviceData` object parameters

Parameter | Type | Description
----- | ----- | -----
`platform` | **string** | Operating system of the device running [WhatsApp Business](https://www.whatsapp.com/business/) application
`deviceManufacturer` | **string** | Device manufacturer
`deviceModel` | **string** | Device model
`osVersion` | **string** | Operating system version
`waVersion` | **string** | Application version [WhatsApp Business](https://www.whatsapp.com/business/) or [WhatsApp](https://www.whatsapp.com/)
`battery` | **integer** | Battery level

### Webhook body example {#webhook-example-body}

```json
{
    "typeWebhook": "deviceInfo",
    "instanceData": {
        "idInstance": 1234,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1586700802,
    "deviceData": {
        "platform": "iphone",
        "deviceManufacturer": "Apple",
        "deviceModel": "iPhone 11",
        "osVersion": "13.4.1",
        "waVersion": "2.20.42",
        "battery": 90
    }
}
```
