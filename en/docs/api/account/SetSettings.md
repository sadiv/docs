# SetSettings

The method is aimed for setting account settings. 

> When this method is requested, the account is rebooted.

## Request {#request}

To set account settings, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Selective specification of parameters is allowed. At least one parameter must be specified.

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`countryInstance` | **string** | No | Account country code in accordance with [ISO 3166-2](https://ru.wikipedia.org/wiki/ISO_3166-2) standard
`webhookUrl` | **string** | No | URL for sending notifications. If it is required to disable getting notifications, then specify an empty string
`webhookUrlToken` | **string** | No | Token to access your notification server, if not required, then specify an empty string 
`delaySendMessagesMilliseconds` | **integer** | No | [Message sending delay](../send-messages-delay.md) is in milliseconds. Minimum value is 500 msec
`markIncomingMessagesReaded` | **string** | No | Mark incoming messages as read or not, possible variants: `yes`,` no`. Ignored if markIncomingMessagesReadedOnReply is 'yes'.
`markIncomingMessagesReadedOnReply` | **string** | No | Mark incoming messages as read when posting a message to the chat via API, possible variants: `yes`,` no`. If it is 'yes', then the markIncomingMessagesReaded setting is ignored.
`proxyInstance` | **string** | No | Proxy for the account in the format {ip}:{port}:{login}:{password}, if you want the account to work on your proxy; system proxies are used by default
`outgoingWebhook` | **string** | No |Get notifications about outgoing messages sending/delivering/reading statuses, possible variants: `yes`,` no`
`outgoingMessageWebhook` | **string** | No |Get notifications about messages sent from the phone, possible variants: `yes`,` no`
`stateWebhook` | **string** | No |Get notifications about the account authorization state change, possible variants: `yes`,` no`
`incomingWebhook` | **string** | No |Get notifications about incoming messages and files, possible variants: `yes`,` no`
`deviceWebhook` | **string** | No |Get notifications about the device (phone) and battery level, possible variants: `yes`,` no`
`statusInstanceWebhook` | **string** | No | Get notifications about the account socket connection status change, possible variants: `yes`,` no`
`sendFromUTC` | **string** | No | Set the account setting - the delay of sending from the queue within the time interval AFTER the specified one (Attention, the time is indicated in UTC), mandatory if specified `sendToUTC`, possible variants: `09:00`
`sendToUTC` | **string** |  No | Set the account setting - the delay of sending from the queue within the time interval BEFORE the specified one (Attention, the time is indicated in UTC), mandatory if specified `sendFromUTC`, possible variants: `12:00`

### General request body example {#request-example-body}

```json
{
    "countryInstance": "ru",
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "webhookUrlToken": "",
    "delaySendMessagesMilliseconds": 1000,
    "markIncomingMessagesReaded": "no",
    "markIncomingMessagesReadedOnReply": "no",
    "proxyInstance": "100.100.100.100:3535:login:password",
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
    "statusInstanceWebhook": "yes" 
}
```
### Request body example for setting time interval {#request-example-body-time-interval}

It is mandatory to specify sendFromUTC and sendToUTC parameters together, otherwise an error will occur.
If you need to send messages only in the interval from 12:00 to 18:00 Moscow time, then you have to specify the following parameter values:

```json
{
    "sendFromUTC": "09:00",
    "sendToUTC": "15:00"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`saveSettings` | **boolean** | Flag that the settings are saved

### Response body example {#response-example-body}

```json
{
    "saveSettings": true
}
```

### SetSettings errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setSettings/{{apiTokenInstance}}"

payload = "{\r\n\t\"countryInstance\": \"ru\",\r\n\t\"webhookUrl\": \"https://mysite.ru\",\r\n\t\"delaySendMessagesMilliseconds\": 1000,\r\n\t\"markIncomingMessagesReaded\": \"no\",\r\n\t\"proxyInstance\": \"123.456.78.910:39898:qGKqCo:Jb26Xz\",\r\n\t\"outgoingWebhook\": \"yes\",\r\n\t\"stateWebhook\": \"yes\",\r\n\t\"incomingWebhook\": \"yes\",\r\n\t\"deviceWebhook\": \"no\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
