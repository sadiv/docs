# Get QR code via websocket

Along with getting a QR code using [QR](QR.md) method, it is possible to get a QR code via websocket connection. Timeout for scanning a QR code is 100 seconds. During this time, the QR code must be scanned. To get a QR code, the account must be in an unauthorized state. If the account is authorized, you have first to log out the account using [Logout](Logout.md) method.

After successful scanning a QR code and authorizing the account, an [incoming notification](../receiving/index.md) in the form of [Account Status](../receiving/notifications-format/StateInstanceChanged.md) is generated.

To get QR code you have to establish a bsocket-connection at: 

```
wss://api.green-api.com/waInstance{{idInstance}}/scanqrcode/{{apiTokenInstance}
```

## Example of getting a QR code in a browser {#request-example-js}

You can see an example of getting a QR code throu wedsocket in the file [websocketExampleQRcode](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCodeWebsocket.html) 

## Response {response}

### Response parameters {#response-parameters}

Parameter | Type | Description
----- | ----- | ----- 
`type` | **string** | Message type, possible variants `qrCode`, `error`, `accountData`, `alreadyLogged`, `timeoutExpired`
`message` | **string** | Message content. Takes on different values depending on parameter `type`


#### Got QR code {#response-type-qrCode}

Parameter | Type |  Descroption
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
`message` | **string** | akes on the value `instance account already authorized`


#### QR code scan timeout expired {#response-type-timeoutExpired}

Parameter | Type |  Description
----- | ----- | ----- 
`type` | **string** | `timeoutExpired` - the timeout within which a QR code must be scanned has expired. Timeout for scanning a QR code is 100 seconds.
`message` | **string** | Takes on the value `timeoutExpired`

#### Authorized account data received {#response-type-accountData}

Parameter | Type |  Description
----- | ----- | ----- 
`type` | **string** | `accountData` - received account data after successful authorization 
`wid` | **string** | Account Id in WhatsApp format
`pushname` | **string** | Account name in WhatsApp
`proxy` | **string** |  Proxy IP address assigned to the account
`webhookUrl` | **string** | Incoming webhooks URL
