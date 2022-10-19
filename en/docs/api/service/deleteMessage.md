# deleteMessage
The method deletes a message from a chat.
## Request {#request}

To delete a message, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/deleteMessage/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [User or group chat Id](../chat-id.md)
`idMessage` | **string** | Yes | Deleted message ID 

### Request body example {#request-example-body}

```json
{
    "chatId": "120363043968066561@g.us",
    "idMessage": "BAE5F4886F6F2D05"
}
```

## Response {#response}

### Response parameters {#response-parameters}

The response body is empty. If successful, the server response is 200.

### DeleteMessage errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

HTTP code | Error identifier | Description
----- | ----- | -----
400 | `chatId not found` | chatID is not found
400 | `ID message notfound` | IDMessage is not found

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/deleteMessage/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"120363043968066561@g.us\, \"idMessage\": \"BAE5F4886F6F2D05\" \"r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
