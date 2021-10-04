# QR

The method is aimed for getting QR code. 
To authorize your account, you have to scan a QR code from application [WhatsApp Business](https://www.whatsapp.com/business/) on your phone.
You can also get a QR code and authorize your account in your profile. The procedure for authorizing an account in your profile is described in section [Before you start](../../before-start.md#qr).

> QR code is updated every 20 seconds, therefore, it is recommended to request the method for getting a QR code with a delay in 1 second.

To get a QR code, the account must have an unauthorized status. If the account is authorized, you have first to log out the account using [Logout](Logout.md) method.
After sucessful scanning a QR code and authorizing the account [incoming notification](../receiving/index.md) in form of [Account Status](../receiving/notifications-format/StateInstanceChanged.md) is generated.

> You can also get a QR code via [websocket-connection](Scanqrcode.md) 

## Request {#request}

To get a QR code, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/qr/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to section [Before you start](../../before-start.md#parameters).


## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`type` | **string** | Message type, possible variants `qrCode`, `error`, `alreadyLogged`
`message` | **string** | Message content. Can have different variants depending on `type`


#### Got QR code {#response-type-qrCode}

Parameter | Type |  Description
----- | ----- | ----- 
`type` | **string** | `qrCode` - got QR code image
`message` | **string** | `base64` QR code image. To display in the browser, you need to add a string `data:image/png;base64, {message}`


#### Error occurred {#response-type-error}

Parameter | Type |  Description
----- | ----- | ----- 
`type` | **string** | `error` - an error is occurred
`message` | **string** | Error description


#### Account already authorized {#response-type-alreadyLogged}

Parameter | Type |  Description
----- | ----- | ----- 
`type` | **string** | `alreadyLogged` - account is already authorized. To get a QR code, you have first to log out of your account using [Logout](Logout.md) method
`message` | **string** | Takes on the value `instance account already authorized`


### QR errors {#errors}

For a list of errors common to all methods, refer to section [Common errors](../common-errors.md)

## Example of getting a QR code in a browser {#request-example-js}

```js
// ...
```

You can also see an example of getting a QR code in a browser in the file [browserExampleQRcode](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCode.html) 

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/qr/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
