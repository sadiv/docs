# Logout

The method is aimed for logging out an account. 

## Request {#request}

To log out the account, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/Logout/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refet to section [Before you begin](../../before-start.md#parameters).

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`isLogout` | **boolean** | WhatsApp account logging out result

### Response body example {#response-example-body}

```json
{
    "isLogout": true
}
```

### Logout errors {#errors}

For a list of errors common to all methods, refer to section [Common errors](../common-errors.md)

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/logout/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
