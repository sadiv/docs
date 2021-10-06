# ClearMessagesQueue

The method is aimed for clearing the queue of messages to be sent.

## Request {#request}

To clear messages queue, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/ClearMessagesQueue/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`isCleared` | **boolean** | Messages queue clearing flag

### Response body example {#response-example-body}

```json
{
    "isCleared": true
}
```

### ClearMessagesQueue errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/clearMessagesQueue/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
