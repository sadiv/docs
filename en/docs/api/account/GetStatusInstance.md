# GetStatusInstance

The method is aimed for getting the status of the account instance socket connection with WhatsApp.

## Request {#request}

To get account socket status, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/getStatusInstance/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to section [Before you start](../../before-start.md#parameters).

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`statusInstance` | **string** | Account socket connection status. Have variants:
| | `online` - Account can get/post messages, socket is open
| | `offline` - Account can't get/post messages, socket is closed


### Response body example {#response-example-body}

```json
{
    "statusInstance": "online"
}
```

### Errors GetStatusInstance {#errors}

For a list of errors common to all methods, refer to section [Common errors](../common-errors.md)

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getStatusInstance/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
