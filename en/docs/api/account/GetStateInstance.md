# GetStateInstance

The method is aimed for getting the account state.

## Request {#request}

To get the account state, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/getStateInstance/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to section [Before you start](../../before-start.md#parameters).

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`stateInstance` | **string** | Account state. Have variants:
| | `notAuthorized` - Account is not authorized. For account authorization refer to section [Before you start](../../before-start.md#qr)
| | `authorized` - Account is authorized
| | `sleepMode` - Account is in sleep mode. The state is possible when the phone is switched off. After the phone is switched on, it may take up to 5 minutes for the account state to be changed to `authorized`.

### Response body example {#response-example-body}

```json
{
    "stateInstance": "authorized"
}
```

### Errors GetStateInstance {#errors}

For a list of errors common to all methods, refer to section [Stansdard errors](../common-errors.md)

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getStateInstance/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
