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
`creation` | **integer** | Время создания группы в Unix-формате
`participants` | **array** | Group participants collection
`subjectTime` | **integer** | Время создания наименования группы в Unix-формате
`subjectOwner` | **string** | [Идентификатор](../chat-id.md#corr) пользователя создавшего наименование группы
`groupInviteLink` | **string** | Group invitation link

Поля объектов из массива `participants`

Parameter | Type |  Description
----- | ----- | ----- 
`id` | **string** | [Идентификатор](../chat-id.md#corr) участника группового чата
`isAdmin` | **boolean** | Флаг, является ли пользователь администратором группы
`isSuperAdmin` | **boolean** | Флаг, является ли пользователь супер администратором группы

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
