# DownloadFile

The method is aimed for downloading incoming and outgoing files.
Links to incoming files are transmitted in [Incoming messages](../notifications-format/incoming-message/Webhook-IncomingMessageReceived.md), and you can also get them using [LastIncomingMessages](../../../api/journals/LastIncomingMessages.md) method.
You can get links to outgoing files using [LastOutgoingMessages](../../../api/journals/LastOutgoingMessages.md) method.

> Files storage period and, accordingly, the capability to download them is limited to 24 hours.

## Request {#request}

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`idMessage` | **string** | Yes | Message Id transmitted in [Incoming messages](../notifications-format/incoming-message/Webhook-IncomingMessageReceived.md) or when sending files using [SendFileByUrl](../../../api/sending/SendFileByUrl.md), [SendFileByUpload](../../../api/sending/SendFileByUpload.md) methods. This parameter is transmitted as the final part of the url request

## Response {#response}

Файл из сообщения

### DownloadFile errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/downloadFile/{{idMessage}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
