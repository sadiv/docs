# AddGroupParticipant

The method adds a participant to a group chat.

## Request {#request}

To add a participant to a group chat, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/AddGroupParticipant/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`groupId` | **string** | Yes | [Group chat Id](../chat-id.md#gus)
`participantChatId` | **string** | Yes | [Id](../chat-id.md#corr) of a participant added to a group chat.

### Request body example {#request-example-body}

Adding a participant to a group chat:
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
`addParticipant` | **boolean** | Adding a participant to a group chat flag

### Response body example {#response-example-body}

```json
{
    "addParticipant": true
}
```

### AddGroupParticipant errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/addGroupParticipant/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"79001234567-1581234048@g.us\",\r\n\t\"participantChatId\": \"79001234568@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
