# ShowMessagesQueue

The method is aimed for getting a list of messages in the queue to be sent. 
Messages sending rate is managed by [Messages sending delay](../send-messages-delay.md) parameter.

## Request {#request}

To get a messages queue, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/ShowMessagesQueue/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Array of objects with parameters:

Parameter | Type |  Description
----- | ----- | ----- 
`typeMessage` | **string** | Message type, possible variants:
| | `textMessage` - text message
| | `imageMessage` - image message
| | `videoMessage` - video message
| | `documentMessage` - document file message
| | `audioMessage` - audio message
| | `locationMessage` - location message
| | `contactMessage` - contact message
| | `extendedTextMessage` - link and preview message
`chatId` | **string** | [Chat Id](../chat-id.md) where the message will be sent to
`message` | **string** |  message text, if `typeMessage` = `textMessage`/`locationMessage`/`contactMessage`/`extendedTextMessage`
`fileName` | **string** | outgoing file name, if `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`/`audioMessage`

### Response body example {#response-example-body}

```json
[
    {
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "message": "I use Green-API to send this message to you!"
    },
    {
        "typeMessage": "imageMessage",
        "chatId": "79001234567@c.us",
        "fileName": "image.jpg"
    }
]
```

### ShowMessagesQueue errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/showMessagesQueue/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
