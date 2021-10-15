# SetSystemProxy

The method is aimed for setting a system proxy. Use the method when you need to reset custom proxy settings to system ones.

## Request {#request}

To set a system proxi, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/SetSystemProxy/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`setSystemProxy` | **boolean** | System proxy setting flag: `true` - system proxy set; `false` - not set

### Response body example {#response-example-body}

```json
{
    "setSystemProxy": true
}
```

### SetSystemProxy errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/SetSystemProxy/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
