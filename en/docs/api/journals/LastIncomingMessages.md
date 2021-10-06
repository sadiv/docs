# LastIncomingMessages

The method returns the last incoming messages of the account.

> The storage period for incoming messages on the server is 24 hours.

## Request {#request}

To get incoming messages, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/lastIncomingMessages/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Array of objects with parameters:

Parameter | Type|  Description
----- | ----- | ----- 
`idMessage` | **string** | Incoming message Id
`timestamp` | **integer** | Message acceptance time in UNIX format
`typeMessage` | **string** | Message type, possible variants:
| | `textMessage` - text message
| | `imageMessage` - image message
| | `videoMessage` - video message
| | `documentMessage` - document file message
| | `audioMessage` - audio message 
| | `locationMessage` - location message
| | `contactMessage` - contact message
| | `extendedTextMessage` - link and preview message
| | `quotedMessage` - quoted message 
`chatId` | **string** | [Chat Id](../chat-id.md), where the message has been received
`senderId` | **string** | Message sender [Id](../chat-id.md#corr) 
`senderName` | **string** | Message sender name
`textMessage` | **string** | Text message, if `typeMessage`=`textMessage`
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
`longitude` | **double** | Долгота локации
`jpegThumbnail` | **string** | `base64`-coded image preview

Parameters of `contact` object:

Parameter | Type|  Description
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
`stanzaId` | **string** | Quoted message ID 
`participant` | **string** | Recipient chat ID

### Response body example {#response-example-body}

```json
[
    {
        "idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
        "timestamp": 1587129319,
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Nikolay",
        "textMessage": "Hi"
    },
    {
        "idMessage": "EA0BD1AE042DC4F3609867126309D67C",
        "timestamp": 1587147598,
        "typeMessage": "imageMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Nikolay",
        "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/EA1BD1AE042DC4F3609867126309D67C",
        "caption": "What do you think?"
    },
    {
		"idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
		"timestamp": 1587129319,
        "typeMessage": "locationMessage",
        "chatId": "71234567891@c.us",
        "senderId": "1234567891@c.us",
        "senderName": "Nikolay",
        "location": {
            "nameLocation": "I'm here, come",
    	    "address": "614111, Perm",
   		    "latitude": 53.9370129,
    		"longitude": 54.8728409,
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wB=="
        }
	},
    {
		"idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
		"timestamp": 1587129319,
        "typeMessage": "contactMessage",
        "chatId": "1234567891@c.us",
        "senderId": "71234567891@c.us",
        "senderName": "Nikolay",
        "contact": {
            "displayName": "Victor Petrov",
    	    "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79099291652:+7 123 456-78-91\nitem1.X-ABLabel:Mobile\nEND:VCARD"
        }
	},
    {
		"idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
		"timestamp": 1587129319,
        "typeMessage": "extendedTextMessage",
        "chatId": "1234567891@c.us",
        "senderId": "71234567891@c.us",
        "senderName": "Nikolay",
        "extendedTextMessage": {
            "text": "https://www.youtube.com/watch?v=9lO06Zxhu8*8*",
    	    "description": "Video clip",
            "title": "Cool video clip",
            "previewType": "video",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wB=="
        }
	},
    {
        "idMessage": "6195B3523153621DFDFC184D3317E80D",
        "timestamp": 1603182280,
        "typeMessage": "quotedMessage",
        "chatId": "71234567891@c.us",
        "senderId": "71234567891@c.us",
        "senderName": "Mine",
        "textMessage": "Quote test",
        "extendedTextMessage": {
            "stanzaId": "3A6424373F90A939B3C8",
            "participant": "71987654321@c.us"
        }
    }
]
```

### LastIncomingMessages errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/lastIncomingMessages/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
