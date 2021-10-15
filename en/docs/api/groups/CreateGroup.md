# CreateGroup

The method is aimed for creating a group chat.

## Request {#request}

To create a group chat, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/CreateGroup/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`groupName` | **string** | Yes | New group chat name
`chatIds` | **array<string>** | Yes | Collection of group participants [Ids](../chat-id.md#corr) 

### Request body example {#request-example-body}

```json
{
    "groupName": "Group created by Green API",
    "chatIds": [
        "79001234568@c.us",
        "79001234569@c.us"
    ]
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`created` | **boolean** | Group creation flag
`chatId` | **string** | [Group chat Id](../chat-id.md#gus)
`groupInviteLink` | **string** | Group invitation link

### Response body example {#response-example-body}

```json
{
    "created": true,
    "chatId": "79001234567-1587570015@g.us",
    "groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### CreateGroup errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/createGroup/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupName\": \"Group created by Green API\",\r\n    \"chatIds\": [\r\n        \"79001234567@c.us\",\r\n        \"79001234568@c.us\"\r\n    ]\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
