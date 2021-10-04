# GetGro# GetGroupData

The method gets group chat data. 

## Request {#request}

To get group chat data, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetGroupData/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance`, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`groupId` | **string** | Yes | [Group chat Id](../chat-id.md#gus)

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
`groupId` | **string** | [Group chat Id](../chat-id.md#gus)
`owner` | **string** | Group owner [Id](../chat-id.md#corr)
`subject` | **string** | Group name
`creation` | **integer** | Group creation time in Unix format 
`participants` | **array** | Group participants collection
`subjectTime` | **integer** | Group name creation time in Unix format
`subjectOwner` | **string** | User [Id](../chat-id.md#corr) who created the group name 
`groupInviteLink` | **string** | Group invitation link

`Participants`array subjects parameters

Parameter | Type |  Description
----- | ----- | ----- 
`id` | **string** | Group chat participant [Id](../chat-id.md#corr)
`isAdmin` | **boolean** | Flag whether the user is a group administrator
`isSuperAdmin` | **boolean** | Flag whether the user is a group super administrator

### Response body example {#response-example-body}

```json
{
	"groupId": "79001234567-1587570015@g.us",
	"owner": "79001234567@c.us",
	"subject": "Green API Group",
	"creation": 1587570015,
	"participants": [
		{
			"id": "79001234567@c.us",
			"isAdmin": true,
			"isSuperAdmin": true
		},
		{
			"id": "79001234568@c.us",
			"isAdmin": true,
			"isSuperAdmin": false
		},
		{
			"id": "79001234569@c.us",
			"isAdmin": false,
			"isSuperAdmin": false
		}
	],
	"subjectTime": 1587737715,
	"subjectOwner": "79001234567@c.us",
	"groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### GetGroupData errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getGroupData/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"79001234567-1587570015@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
