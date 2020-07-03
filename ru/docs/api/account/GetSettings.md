# GetSettings

Метод предназначен для получения текущих настроек аккаунта.

## Запрос {#request}

Для получения текущих настроек аккаунта требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetSettings/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](/before-start#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`wid` | **string** | Идентификатор аккаунта в Whatsapp
`countryInstance` | **string** | Код страны аккаунта по стандарту ISO 3166-2
`typeAccount` | **string** | Тип аккаунта, возможные значения trial || production || vip;
`webhookUrl` | **string** | Установленный URL для получения webhook уведомлений
`delaySendMessagesMilliseconds` | **integer** | Задержка между отправкой исходящих сообщений в миллисекундах
`markIncomingMessagesReaded` | **string** | Отмечать входящие сообщения прочитанными или нет, возможные значения yes/no
`proxyInstance` | **string** | Параметры прокси аккаунта, отдается в зависимости от настроек прокси. Если прокси собственное, отдаются все параметры в виде ip:port:login:password. Если прокси системное, отдается в зависимости от настроек прокси у партнера или системных. И может быть в виде  ip:port:login:password или “system proxy”.
`outgoingWebhook` | **string** | Получать webhook уведомления об отправке/доставке/прочтении исходящих сообщений, возможные значения yes/no
`stateWebhook` | **string** | Получать webhook уведомления об изменении состояние авторизации аккаунта, возможные значения yes/no
`incomingWebhook` | **string** | Получать webhook уведомления о входящих сообщениях и файлах, возможные значения yes/no
`deviceWebhook` | **string** | Получать webhook уведомления об устройстве и уровне заряда батареи, возможные значения yes/no

### Пример тела ответа {#response-example-body}

```json
{
    "wid": "1234567891@c.us", 
    "countryInstance": "ru",
    "typeAccount": "vip",
    "webhookUrl": "https://webhook.com",
    "delaySendMessagesMilliseconds": 3000,
    "markIncomingMessagesReaded": "yes",
    "proxyInstance": "123.45.67.891:3435:hdhhd:i3ji3",
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
}
```

### Ошибки GetSettings {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getSettings/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```