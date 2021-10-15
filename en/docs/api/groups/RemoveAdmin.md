# RemoveAdmin

The method removes a participant from group chat administartion rights. 

## Request {#request}

To remove a participant from group chat administartion rights, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/RemoveAdmin/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`groupId` | **string** | Yes | [Group chat Id](../chat-id.md#gus)
`participantChatId` | **string** | Yes | [Id](../chat-id.md#corr) of a group participant, who you'd like to remove from group administration rights

### Request body example {#request-example-body}

Removing a participant from group administration rights:
```json
{
    "groupId": "79001234567-1587570015@g.us",
    "participantChatId": "79001234565@c.us"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`removeAdmin` | **boolean** | Flag of removing a group participant from administration rights 

### Response body example {#response-example-body}

```json
{
    "removeAdmin": true
}
```

### RemoveAdmin errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/removeAdmin/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"79001234567-1587570015@g.us\",\r\n    \"participantChatId\": \"79001234568@c.us\",\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
