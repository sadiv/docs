# Reboot

The method is aimed for rebooting an account.

## Request {#request}

To reboot the account, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/Reboot/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`isReboot` | **boolean** | Result of rebooting WhatsApp account

### Response body example {#response-example-body}

```json
{
    "isReboot": true
}
```

### Reboot errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/reboot/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
