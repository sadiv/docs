# GetChatHistory

The method returns the chat message history.

> **Important:** Message history is stored and retrieved from the telephone, so it is important that the telephone is available. If the phone loses connection, the method request may end with an HTTP `504` error. 

## Request {#request}

To get chat history, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetChatHistory/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameterss, please refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Personal or chat Id](../chat-id.md) the message history of which you need to get
`count ` | **integer** | No | The number of messages to get. The default is `100`  

### Request body example {#request-example-body}

10 last messages request:
```json
{
    "chatId": "79001234567@c.us",
    "count": 10
}
```

## Response {#response}

The response contains a list of all received and sent messages in the chat. Message time stamp descending-order sort.

### Response parameters {#response-parameters}

Array of objects with parameters:

Parameter | Type |  Description
----- | ----- | ----- 
`type` | **string** | Message type: `outgoing` - outgoing message; `incoming` - incoming message
`timestamp` | **integer** | Time when the message has been sent in UNIX format
`idMessage` | **string** | Message Id
`statusMessage` | **string** | Outgoing message status. Present only for `type` = `outgoing`. Possible variants:
| | `sent` - sent
| | `delivered` - delivered
| | `read` - read/seen/heard
`typeMessage` | **string** | Message type, possible variants:
| | `textMessage` - text message
| | `imageMessage` - image message
| | `videoMessage` - video message
| | `documentMessage` - document file message
| | `audioMessage` - audio message
| | `locationMessage` - сообщение геолокации
| | `contactMessage` - contact message
| | `extendedTextMessage` - link and preview message
`chatId` | **string** | [Chat Id](../chat-id.md)
`senderId` | **string** | Incoming message sender [Id](../chat-id.md#corr). Present only for `type` = `incoming`
`senderName` | **string** | Incoming message sender name. Present only for `type` = `incoming`
`textMessage` | **string** | Message text, if `typeMessage`=`textMessage`
`downloadUrl` | **string** | Link to download a file, if `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`/`audioMessage`
`caption` | **string** |File caption, if `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`
`location` | **object** | Location structure object, if `typeMessage`=`locationMessage`
`contact` | **object** | Contact structure object, if `typeMessage`=`contactMessage`
`extendedTextMessage` | **object** | Link data structure object, if `typeMessage`=`extendedTextMessage`

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
        "type": "incoming",
        "timestamp": 1603964449,
        "idMessage": "3AADDD555CB0822C0539",
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Andrew Sh",
        "textMessage": "I use Green-API to get this message from you!"
    },
    {
        "type": "outgoing",
        "timestamp": 1603964445,
        "idMessage": "3EB08816FEBCCC3FACD2",
        "statusMessage": "read",
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "textMessage": "I use Green-API to send this message to you!"
    },
    {
        "type": "incoming",
        "timestamp": 1603964444,
        "idMessage": "3AA45F9F285C5249CDFC",
        "typeMessage": "imageMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Andrew Sh",
        "downloadUrl": "https://api.green-api.com/waInstance9075/downloadFile/download-file-id",
        "caption": "Green-API Logo"
    }
]
```

### GetChatHistory errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/GetChatHistory/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"count\": 100\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
