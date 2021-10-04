# UpdateGroupName

The method changes a group chat name.

## Request {#request}

To change a group chat name, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/UpdateGroupName/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`groupId` | **string** | Yes | [Group chat Id](../chat-id.md#gus)
`groupName` | **string** | Yes | Group chat name

### Request body example {#request-example-body}

```json
{
    "groupId": "79001234567-1587570015@g.us",
    "groupName": "Group created by Green API+"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`updateGroupName` | **boolean** | Group name change flag

### Response body example {#response-example-body}

```json
{
    "updateGroupName": true
}
```

### UpdateGroupName errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/updateGroupName/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"12345678910-1112131415@g.us\",\r\n    \"groupName\":\"Group created by Green API\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
