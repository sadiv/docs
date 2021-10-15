# SendLink

The method is aimed for sending a message with a link, by which an image preview, title and description will be added. 
Image, title and description are obtained from [Open Graph](https://en.wikipedia.org/wiki/Facebook_Platform#Open_Graph_protocol) page template being linked to.
The message will be added to the send queue. The rate at which messages are sent from the queue is managed by [Messages sending delay](../send-messages-delay.md) parameter.

## Request {#request}

To send a link message, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/sendLink/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`urlLink` | **string** | Yes | Link address
`quotedMessageId` | **string** | No | Quoted message ID. If present, the message will be sent quoting the specified chat message

> It is recommended that the page referred to with `urlLink` contains [Open Graph](https://en.wikipedia.org/wiki/Facebook_Platform#Open_Graph_protocol) template. In this case, the message will be supplemented with an image, a title and a short description.

### Request body example {#request-example-body}

Sending a message to a personal chat:
```json
{
    "chatId": "79001234567@c.us",
    "urlLink": "https://green-api.com"
}
```

Sending a message to a group chat:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "urlLink": "https://green-api.com"
}
```

Sending a message to a personal chat:
```json
{
    "chatId": "79001234567@c.us",
    "urlLink": "https://green-api.com",
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

### SendLink errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLink/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"urlLink\": \"https://green-api.com\"\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
