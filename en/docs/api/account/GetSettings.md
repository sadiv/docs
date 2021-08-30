# GetSettings

Метод предназначен для получения текущих настроек аккаунта.

## Запрос {#request}

Для получения текущих настроек аккаунта требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetSettings/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`wid` | **string** | Идентификатор аккаунта в WhatsApp
`countryInstance` | **string** | Код страны аккаунта по стандарту [ISO 3166-2](https://ru.wikipedia.org/wiki/ISO_3166-2)
`typeAccount` | **string** | Тип аккаунта, возможные значения: `trial`, `production`, `vip`
`webhookUrl` | **string** | URL для получения входящих уведомлений
`delaySendMessagesMilliseconds` | **integer** | [Интервал отправки сообщений](../send-messages-delay.md) в миллисекундах
`markIncomingMessagesReaded` | **string** | Отмечать входящие сообщения прочитанными или нет, возможные значения: `yes`, `no`
`proxyInstance` | **string** | Параметры прокси аккаунта. Отображаются в зависимости от настроек прокси. Если прокси собственное, отдаются все параметры в виде `ip:port:login:password`. Если прокси системное, отдается в зависимости от системных настроек прокси. Может принимать значения: `ip:port:login:password` или `system proxy`.
`outgoingWebhook` | **string** | Получать уведомления о статусах отправки/доставки/прочтении исходящих сообщений, возможные значения: `yes`, `no`
`outgoingMessageWebhook` | **string** | Получать уведомления о сообщениях, отправленных с телефона, возможные значения: `yes`, `no`
`stateWebhook` | **string** | Получать уведомления об изменении состояния авторизации аккаунта, возможные значения: `yes`, `no`
`incomingWebhook` | **string** | Получать уведомления о входящих сообщениях и файлах, возможные значения: `yes`, `no`
`deviceWebhook` | **string** | Получать уведомления об устройстве (телефоне) и уровне заряда батареи, возможные значения: `yes`, `no`

### Пример тела ответа {#response-example-body}

```json
{
    "wid": "79001234567@c.us", 
    "countryInstance": "ru",
    "typeAccount": "vip",
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "delaySendMessagesMilliseconds": 3000,
    "markIncomingMessagesReaded": "yes",
    "proxyInstance": "123.45.67.891:3435:hdhhd:i3ji3",
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```

### Ошибки GetSettings {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getSettings/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```