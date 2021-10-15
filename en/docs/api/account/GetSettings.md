# GetSettings

The method is aimed for getting the current account settings.

## Request {#request}

To get the current account settings you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetSettings/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, please refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`wid` | **string** | Account ID in WhatsApp
`countryInstance` | **string** | Account country code in accordance with standard [ISO 3166-2](https://ru.wikipedia.org/wiki/ISO_3166-2)
`typeAccount` | **string** | Account type, possible variants: `trial`, `production`, `vip`
`webhookUrl` | **string** | URL to receive incoming notifications
`webhookUrlToken` | **string** | Token for connecting to your webhook server
`delaySendMessagesMilliseconds` | **integer** | [Message sending delay](../send-messages-delay.md) is in milliseconds
`markIncomingMessagesReaded` | **string** | Mark incoming messages as read or not, possible variants: `yes`, `no`. Ignored if markIncomingMessagesReadedOnReply is 'yes'.
`markIncomingMessagesReadedOnReply` | **string** | Mark incoming messages as read when sending a message to the chat via API, possible variants: `yes`, `no`. If 'yes', then markIncomingMessagesReaded setting is ignored.
`proxyInstance` | **string** | Account proxy parameters. Displayed depending on proxy settings. If the proxy is your own, all parameters are given as follows:  `ip:port:login:password`. If the proxy is system, it is given depending on proxy system settings. Can have the following variants: `ip:port:login:password` or `system proxy`.
`outgoingWebhook` | **string** | Get notifications about outgoing messages sending / delivering / reading status, possible variants: `yes`, `no`
`outgoingMessageWebhook` | **string** | Get notifications about messages sent from phone, possible variants: `yes`, `no`
`stateWebhook` | **string** | Get notifications about changes in the account authorization status, possible variants: `yes`, `no`
`incomingWebhook` | **string** | Get notifications about incoming messages and files, possible variants: `yes`, `no`
`deviceWebhook` | **string** | Get notifications about the device (phone) and battery level, possible variants: `yes`, `no`
`statusInstanceWebhook` | **string** | Get notifications about the account socket connection status change, possible variants: `yes`, `no`
`sendFromUTC` | **string** | Get the account setting - the delay of sending from the queue within the time interval AFTER the specified one (Attention, the time is indicated in UTC), possible variants: `09:00`
`sendToUTC` | **string** |  Get the account setting - the delay of sending from the queue within the time interval BEFORE the specified one (Attention, the time is indicated in UTC), possible variants: `12:00`

### Response body example {#response-example-body}

```json
{
    "wid": "79001234567@c.us", 
    "countryInstance": "ru",
    "typeAccount": "vip",
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "webhookUrlToken": "",
    "delaySendMessagesMilliseconds": 3000,
    "markIncomingMessagesReaded": "yes",
    "markIncomingMessagesReadedOnReply": "no",
    "proxyInstance": "123.45.67.891:3435:hdhhd:i3ji3",
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
    "statusInstanceWebhook": "yes",
    "sendFromUTC": "12:00",
    "sendToUTC": "18:00"
}
```

### Errors GetSettings {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getSettings/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
