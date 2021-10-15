# CheckWhatsapp

The method checks WhatsApp account availability on a phone number.

## Request {#request}

To check WhatsApp account availability, you have to execute request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/CheckWhatsapp/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`phoneNumber` | **integer** | Yes | Recipient's phone number in international format: 11 or 12 digits; Example: `79001234567` or `380123456789`

### Request body example {#request-example-body}

```json
{
    "phoneNumber": 79001234567
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`existsWhatsapp` | **boolean** | Flag of WhatsApp availability on a phone number 

### Response body example {#response-example-body}

```json
{
    "existsWhatsapp": true
}
```

### CheckWhatsapp errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

HTTP code | Error Id | Description
----- | ----- | -----
400 | `bad phone number, valid 11 or 12 digits` | Invalid phone number format, must be 11 or 12 digits
400 | `check phone number timeout limit exceeded` | The timeout for a response to check a phone number has been exceeded

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/checkWhatsapp/{{apiTokenInstance}}"

payload = "{\r\n    \"phoneNumber\": 79001234567\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
