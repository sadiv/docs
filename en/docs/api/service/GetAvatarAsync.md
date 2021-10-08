# GetAvatarAsync

The method returns asynchronously the avatar of a correspondent or a group chat. Unlike [GetAvatar](GetAvatar) method, the request result is returned as a webhook AvatarInfo

## Request {#request}

To get avatar, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetAvatarAsync/{{apiTokenInstance}}
```

For `idInstance` or `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Correspondent or group chat Id](../chat-id.md)

### Request body example {#request-example-body}

To get your avatar - specify your number in chatId ("{your number}@c.us").

Get correspondent's avatar:
```json
{
    "chatId": "79001234567@c.us"
}
```

Get group chat avatar:
```json
{
    "chatId": "79001234567-1581234048@g.us"
}
```

## Response {#response}

Successful request returns an empty response with status 200

### GetAvatar errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

HTTP code | Error Id | Description
----- | ----- | -----
200|`bad request data`| Invalid phone number format. Telephone number must be 11 or 12 digits. Or chat Id

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getAvatarAsync/{{apiToFor a list of errors common to all methods, refer to kenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

requests.request("POST", url, headers=headers, data = payload)

```
