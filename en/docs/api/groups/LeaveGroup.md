# LeaveGroup

The method makes the current account user leave the group chat. 

## Request {#request}

To leave a group chat, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/LeaveGroup/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`groupId` | **string** | Yes | [Group chat Id](../chat-id.md#gus), which you'd like to leave.

### Request body example {#request-example-body}

```json
{
    "groupId": "79001234567-1587570015@g.us"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`leaveGroup` | **boolean** | Leave group flag

### Response body example {#response-example-body}

```json
{
    "leaveGroup": true
}
```

### LeaveGroup errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/leaveGroup/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"79001234567-1587570015@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
