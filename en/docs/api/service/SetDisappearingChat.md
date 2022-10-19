# Set Disappearing Chat


The method is aimed for changing settings of disappearing messages in chats. The standard settings of the application are used: 0 (off), 86400 (24 hours), 604800 (7 days), 7776000 (90 days).

## Request {#request}

To set settings, you have to execute a request at:

```
POST https://api.green-api.com/waInstance{{idInstance}}/setDisappearingChat/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Correspondent id](../chat-id.md)
`ephemeralExpiration` | **integer** | No | Messages lifetime in seconds, takes on the values: 0, 86400, 604800, 7776000

### Request body example {#request-example-body}

```json
{
    "chatId": "71234567890@c.us",
    "ephemeralExpiration": 0
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`chatId` | **string** | yes | [Correspondent id](../chat-id.md)
`disappearingMessagesInChat` | **boolean** | Chat state (disappearing or plain), takes on the values: true, false
`ephemeralExpiration` | **integer** | Messages lifetime in chats, takes on the values: 0, 86400, 604800, 7776000

### Response body example {#response-example-body}


```json
{
    "chatId": "712345678910@c.us",
    "disappearingMessagesInChat": false,
    "ephemeralExpiration": 0
}
```

### SetDisappearingChat errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md)

## Python request example  {#request-example-python}

```

import requests
import json

url = "https://api.green-api.com/waInstance{{idInstance}}/setDisappearingChat/{{apiTokenInstance}}
"
payload = json.dumps({
  "chatId": "712345678910@c.us",
  "ephemeralExpiration": 0
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)


```

