# GetAvatar

The method returns the avatar of a correspondent or a group chat.

## Request {#request}

To get avatar, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetAvatar/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Correspondent or group chat Id](../chat-id.md)

### Request body example {#request-example-body}

To get your avatar - specify your number in chatId ("{your number}@c.us").

Get the correspondent's avatar:
```json
{
    "chatId": "79001234567@c.us"
}
```

Get a group chat avatar:
```json
{
    "chatId": "79001234567-1581234048@g.us"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`existsWhatsapp` | **boolean** | Flag of WhatsApp account availability on the correspondent's phone number
`urlAvatar` | **string** | Link to a correspondent or a group chat avatar. The parameter takes an empty value if the avatar is not set or the correspondent does not have a WhatsApp account (`existsWhatsapp`=`false`)
`reason` | **string** | Reason why avatar has not been checked. Присутствует когда не удалось выполнить проверку, possible variants:
| | `bad request data` - Invalid phone number format. Telephone number must be 11 or 12 digits. Or chat Id
| | `get avatar timeout limit exceeded` - The timeout for a response to check avatar availabiity has been exceeded

### Response body example {#response-example-body}

```json
{
  	"existsWhatsapp": true,
 	  "urlAvatar": "https://pps.whatsapp.net/v/link/to/the/image"
}
```

### GetAvatar errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

HTTP code | Error Id | Description
----- | ----- | -----
200|`bad request data`| Invalid phone number format. Telephone number must be 11 or 12 digits. Or chat Id
200|`get avatar timeout limit exceeded`| The timeout for a response to check avatar availabiity has been exceeded

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getAvatar/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
