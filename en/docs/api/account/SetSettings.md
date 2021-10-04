# SetSettings

The method is aimed for setting account settings. 

> When this method is requested, the account is rebooted.

## Request {#request}

To set account settings, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Selective specification of parameters is allowed. At least one parameter must be specified.

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`countryInstance` | **string** | No | Account country code in accordance with [ISO 3166-2](https://ru.wikipedia.org/wiki/ISO_3166-2) standard
`webhookUrl` | **string** | No | URL for sending notifications. If it is required to disable getting notifications, then specify an empty string
`webhookUrlToken` | **string** | No | Token to access your notification server, if not required, then specify an empty string 
`delaySendMessagesMilliseconds` | **integer** | No | [Message sending delay](../send-messages-delay.md) is in milliseconds. Minimum value is 500 msec
`markIncomingMessagesReaded` | **string** | No | Mark incoming messages as read or not, possible variants: `yes`,` no`. Ignored if markIncomingMessagesReadedOnReply is 'yes'.
`markIncomingMessagesReadedOnReply` | **string** | No | Mark incoming messages as read when posting a message to the chat via API, possible variants: `yes`,` no`. If it is 'yes', then the markIncomingMessagesReaded setting is ignored.
`proxyInstance` | **string** | No | Прокси для аккаунта в формате `{ip}:{port}:{login}:{password}`, если вы хотите что бы аккаунт работал на вашем прокси, по умолчанию используются системные прокси
`outgoingWebhook` | **string** | No |Получать уведомления о статусах отправки/доставки/прочтении исходящих сообщений, возможные значения: `yes`, `no`
`outgoingMessageWebhook` | **string** | No |Получать уведомления о сообщениях, отправленных с телефона, возможные значения: `yes`, `no`
`stateWebhook` | **string** | No |Получать уведомления об изменении состояния авторизации аккаунта, возможные значения: `yes`, `no`
`incomingWebhook` | **string** | No |Получать уведомления о входящих сообщениях и файлах, возможные значения: `yes`, `no`
`deviceWebhook` | **string** | No |Получать уведомления об устройстве (телефоне) и уровне заряда батареи, возможные значения: `yes`, `no`
`statusInstanceWebhook` | **string** | No | Получать уведомления об изменении состояния сокет соединения аккаунта, возможные значения: `yes`, `no`
`sendFromUTC` | **string** | No | Установить настройку аккаунта интервал отправки из очереди в промежуток времени ОТ указанного (Внимание, время указано в UTC), обязателен, если указано `sendToUTC`, возможные значения: `09:00`
`sendToUTC` | **string** |  No | Установить настройку аккаунта интервал отправки из очереди в промежуток времени ДО указанного (Внимание, время указано в UTC), обязателен, если указано `sendFromUTC`, возможные значения: `12:00`

### Пример тела запроса общий {#request-example-body}

```json
{
    "countryInstance": "ru",
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "webhookUrlToken": "",
    "delaySendMessagesMilliseconds": 1000,
    "markIncomingMessagesReaded": "no",
    "markIncomingMessagesReadedOnReply": "no",
    "proxyInstance": "100.100.100.100:3535:login:password",
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
    "statusInstanceWebhook": "yes" 
}
```
### Пример тела запроса для установки временного интервала {#request-example-body-time-interval}

Обязательно указывать параметры sendFromUTC и sendToUTC вместе, в противном случае возникнет ошибка.
Если требуется отправлять сообщения только в интервале с 12:00 до 18:00 по мск, то требуется указать такие значения параметров:

```json
{
    "sendFromUTC": "09:00",
    "sendToUTC": "15:00"
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`saveSettings` | **boolean** | Flag that the settings are saved

### Response body example {#response-example-body}

```json
{
    "saveSettings": true
}
```

### SetSettings errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setSettings/{{apiTokenInstance}}"

payload = "{\r\n\t\"countryInstance\": \"ru\",\r\n\t\"webhookUrl\": \"https://mysite.ru\",\r\n\t\"delaySendMessagesMilliseconds\": 1000,\r\n\t\"markIncomingMessagesReaded\": \"no\",\r\n\t\"proxyInstance\": \"123.456.78.910:39898:qGKqCo:Jb26Xz\",\r\n\t\"outgoingWebhook\": \"yes\",\r\n\t\"stateWebhook\": \"yes\",\r\n\t\"incomingWebhook\": \"yes\",\r\n\t\"deviceWebhook\": \"no\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
