# SendFileByUrl

The method is aimed for sending a file uploaded by Url.
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
POST https://api.green-api.com/waInstance{{idInstance}}/SendFileByUrl/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`urlFile` | **string** | Yes | Link to outgoing file
`fileName` | **string** | Yes | File name. Must contain the file extension
`caption` | **string** | No | File caption. Caption added to video, images.
`quotedMessageId` | **string** | No | Quoted message ID. If present, the message will be sent quoting the specified chat message
`archiveChat` | **boolean** | No | Archives the chat to which the message was sent. Takes value: true|false

### Request body example {#request-example-body}

Sending a message to a personal chat:
```json
{
    "chatId": "79001234567@c.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Little horse"
}
```

Sending a message to a group chat:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Little horse"
}
```

Sending a quoted message:
```json
{
    "chatId": "79001234567@с.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Little horse",
    "quotedMessageId": "361B0E63F2FDF95903B6A9C9A102F34B"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`idMessage ` | **string** | Outgoing message Id 

### Response body example {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### SendFileByUrl errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendFileByUrl/{{apiTokenInstance}}"

payload = "{\r\n   \t\"chatId\": \"79001234567@c.us\",\r\n\t\"urlFile\": \"https://avatars.mds.yandex.net/get-pdb/477388/77f64197-87d2-42cf-9305-14f49c65f1da/s375\",\r\n\t\"fileName\": \"horse.png\",\r\n\t\"caption\": \"little horse\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
