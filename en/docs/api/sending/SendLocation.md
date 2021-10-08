# SendLocation

The method is aimed for sending location message. 
The message will be added to the send queue. 
The rate at which messages are sent from the queue is managed by [Message sending delay](../send-messages-delay.md) parameter.

## Request {#request}

To send location message, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/sendLocation/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`nameLocation` | **string** | No | Location name
`address` | **string** | No | Location address
`latitude` | **double** | Yes | Location latitude
`longitude` | **double** | Yes | Location longitude
`quotedMessageId` | **string** | No | Quoted message Id, if present the message will be sent quoting the specified chat message

### Request body example {#request-example-body}

Sending messages to a personal chat:
```json
{
    "chatId": "79001234567@c.us",
    "nameLocation": "Restaurant",
    "address": "123456, Perm",
    "latitude": 12.3456789,
    "longitude": 10.1112131
}
```

Sending messages to a group chat:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "nameLocation": "Restaurant",
    "address": "123456, Perm",
    "latitude": 12.3456789,
    "longitude": 10.1112131
}
```

Sending quoted messages:
```json
{
    "chatId": "79001234567@c.us",
    "nameLocation": "Restaurant",
    "address": "123456, Perm",
    "latitude": 12.3456789,
    "longitude": 10.1112131,
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

### SendLocation errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLocation/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567@c.us\",\r\n    \"nameLocation\": \"Я здесь, приезжай\",\r\n    \"address\": \"613123, Perm\",\r\n   \t\"latitude\": 44.9370129,\r\n    \"longitude\": 89.8728409\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
