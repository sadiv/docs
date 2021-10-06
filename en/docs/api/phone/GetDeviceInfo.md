# GetDeviceInfo

The method is aimed for getting information about the device (phone) running [WhatsApp Business](https://www.whatsapp.com/business/) application.

## Request {#request}

To get device info, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetDeviceInfo/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`platform` | **string** | Operating system of the device running [WhatsApp Business](https://www.whatsapp.com/business/) application
`deviceManufacturer` | **string** | Device manufacturer
`deviceModel` | **string** | Device model
`osVersion` | **string** | Operating system version
`waVersion` | **string** | Application version - [WhatsApp Business](https://www.whatsapp.com/business/) or [WhatsApp](https://www.whatsapp.com/)
`battery` | **integer** | Battery level

### Response body example {#response-example-body}

```json
{
    "platform": "iphone",
    "deviceManufacturer": "Apple",
    "deviceModel": "iPhone 11",
    "osVersion": "13.4.1",
    "waVersion": "2.20.42",
    "battery": 90
}
```

### GetDeviceInfo errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getDeviceInfo/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
