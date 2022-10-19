# SendFileByUpload

The method is aimed for sending a file uploaded by form (form-data).
The message will be added to the send queue.
The rate at which messages are sent from the queue is managed by [Message sending delay](../send-messages-delay.md) parameter.

Video, audio and image files available for viewing and listening to are sent as in native-mode WhatsApp. 
Documents are sent in the same way as in native-mode WhatsApp. 
Outgoing file type and send method is determined by the file extension. 
Description is only added to images and video. 

> The maximum size of outgoing files is 37 MB. 

## Request {#request}

To send a file, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendFileByUpload/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`file` | **file** | Yes | Outgoing file
`fileName` | **string** | No| File name. Must contain file extension.
`caption` | **string** | No | File caption. Caption added to video, images. 
`quotedMessageId` | **string** | No | Quoted message Id. If present, the message will be sent quoting the specified chat message.

### Request body example {#request-example-body}

Python request example

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendFileByUpload/{{apiTokenInstance}}"

payload = {'chatId': '79001234567@c.us',
'caption': 'Description'}
files = [
  ('file', open('/C:/window.jpg','rb'))
]
headers= {}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

print(response.text.encode('utf8'))
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`idMessage ` | **string** | Sent message Id 

### Response body example {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### SendFileByUpload errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section
