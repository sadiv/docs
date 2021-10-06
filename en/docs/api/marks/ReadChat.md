# ReadChat

The method is aimed for marking messages in a chat as read. Either all messages or a specified message in a chat can be marked as read.

## Request {#request}

To mark messages in a chat as read, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/ReadChat/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`idMessage` | **string** | No | ID of the incoming message to be marked as read. If not specified, then all unread messages in the chat will be marked as read.

### Request body example {#request-example-body}

Read mark of a single message in the chat:
```json
{
    "chatId": "79001234567@c.us",
    "idMessage": "B275A7AA0D6EF89BB9245169BDF174E6"
}
```

Read mark of all messages in the chat:
```json
{
    "chatId": "79001234567@c.us"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`setRead` | **boolean** | Messages read mark flag

### Response body example {#response-example-body}

```json
{
    "setRead": true
}
```

### ReadChatMessage errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/readChat/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"idMessage\": \"B275A7AA0D6EF89BB9245169BDF174E6\"\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```
