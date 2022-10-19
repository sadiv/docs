# LastOutgoingMessages

The method returns the last outgoing messages of the account. In the default mode the last messages for 24 hours are returned.

## Request {#request}

To get outgoing messages, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/LastOutgoingMessages/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Параметры URL запроса {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`minutes` | **integer** | No | time in minutes for which the messages should be displayed (default is 1440 minutes)


## Response {#response}

### Response parameters {#response-parameters}

Array of objects with parameters:

Parameter | Type |  Description
----- | ----- | ----- 
`idMessage` | **string** | Outgoing message Id
`timestamp` | **integer** | Time of the last action on a message in UNIX format
`statusMessage` | **string** | Outgoing message status, possible variants:
| | `noAccount` - no WhatsApp account on phone number 
| | `notInGroup` - not in this group
| | `sent` - sent
| | `delivered` - delivered
| | `read` - read/seen/heard
`typeMessage` | **string** | Message type, possible variants:
| | `textMessage` - text message
| | `imageMessage` - image message
| | `videoMessage` - video message
| | `documentMessage` - document file message
| | `audioMessage` - audio message
| | `locationMessage` - location message
| | `contactMessage` - contact message
| | `extendedTextMessage` - link and preview message
`chatId` | **string** | [Chat Id](../chat-id.md), where message has been sent to
`textMessage` | **string** | Message text, if `typeMessage`=`textMessage`
`downloadUrl` | **string** | Link to download a file, if `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`/`audioMessage`
`caption` | **string** | File caption
`location` | **object** | Location structure object
`contact` | **object** | Contact structure object
`extendedTextMessage` | **object** | Link data structure object

Parameters of `location` object:

Parameter | Type |  Description
----- | ----- | ----- 
`nameLocation` | **string** | Location name
`address` | **string** | Location address
`latitude` | **double** | Location latitude
`longitude` | **double** | Location longitude
`jpegThumbnail` | **string** | `base64`-coded image preview

Parameters of `contact` object:

Parameter | Type |  Description
----- | ----- | ----- 
`displayName` | **string** | Contact display name
`vcard` | **string** | VCard structure (contact visit card)

Parameters of `extendedTextMessage` object:

Parameter | Type |  Description
----- | ----- | ----- 
`text` | **string** | Link text
`description` | **string** | Link description
`title` | **string** | Link title
`previewType` | **string** | Link preview type
`jpegThumbnail` | **string** | `base64`-coded image preview

### Response body example {#response-example-body}

```json
[
    {
        "idMessage": "3EB0BDDC94BFDFB3D4FA",
        "timestamp": 1587133830,
        "statusMessage": "read",
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "textMessage": "Hi",
    },
    {
        "idMessage": "3EB0BDDC94BFDFB3D4FA",
        "timestamp": 1587133830,
        "statusMessage": "read",
        "typeMessage": "imageMessage",
        "chatId": "79001234567@c.us",
        "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/3EB0BDDC94BFDFB3D4FA",
        "caption": "What do you think?"
    }
]
```

### LastOutgoingMessages errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/lastOutgoingMessages/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
