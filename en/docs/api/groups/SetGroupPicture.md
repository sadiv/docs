# SetGroupPicture

The method sets a group picture.

## Request {#request}

To set a group chat picture, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/setGroupPicture/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`file` | **file** | Yes | Sent file in *.jpg
`groupId` | **string** | Yes | [Group chat Id](../chat-id.md#gus)

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setGroupPicture/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"12345678910-1112131415@g.us\",\r\n}"
files=[
  ('file',('{{file}}.jpeg',open('/C:/{{file}}.jpeg','rb'),'image/jpeg'))
]
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload, files=files)

print(response.text.encode('utf8'))
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`setGroupPicture` | **boolean** | флаг результата установки аватара группы
`urlAvatar` | **string** | url  на установленное изображение
`reason` | **string** | причина почему аватар не был установлен

### Response body example {#response-example-body}

```json
{
    "setGroupPicture": true,
    "urlAvatar": "https://pps.whatsapp.net/v/t61.24694-24/138639660_724754321806449_9118612187814397965_n.jpg?oh=997b0bb13b6bbb750432a86d4b8d935d&oe=600****BB4",
	"reason": ""
}

```

### SetGroupPicture errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

