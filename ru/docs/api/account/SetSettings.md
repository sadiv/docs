# SetSettings

Метод предназначен для смены настроек аккаунта. При вызове данного метода аккаунт перезапускается.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`countryInstance` | **string** | Если не указаны другие параметры | Код страны аккаунта по стандарту ISO 3166-2
`webhookUrl` | **string** | Если не указаны другие параметры | URL для отправки webhook оповещений, если необходимо убрать webhook url, необходимо в качестве значения указать пустую строку
`delaySendMessagesMilliseconds` | **integer** | Если не указаны другие параметры | задержка между отправкой исходящих сообщений в миллисекундах (), минимальное значение 500 мс.;
`markIncomingMessagesReaded` | **string** | Если не указаны другие параметры | Отмечать входящие сообщения прочитанными или нет, возможные значения yes/no
`proxyInstance` | **string** | Если не указаны другие параметры | Прокси для аккаунта ({ip}:{port}:{login}:{password}), если вы хотите что бы аккаунт работал на вашем прокси, по умолчанию используются системные прокси
`outgoingWebhook` | **string** | Если не указаны другие параметры | Получать webhook уведомления об отправке/доставке/прочтении исходящих сообщений, возможные значения yes/no
`stateWebhook` | **string** | Если не указаны другие параметры | Получать webhook уведомления об изменении состояние авторизации аккаунта, возможные значения yes/no
`incomingWebhook` | **string** | Если не указаны другие параметры | Получать webhook уведомления о входящих сообщениях и файлах, возможные значения yes/no
`deviceWebhook ` | **string** | Если не указаны другие параметры | Получать webhook уведомления об устройстве и уровне заряда батареи, возможные значения yes/no

### Пример тела запроса {#request-example-body}

```json
{
    "countryInstance": "uk",
    "webhookUrl": "https://mysite.ru",
    "delaySendMessagesMilliseconds": 1000,
    "markIncomingMessagesReaded": "no",
    "proxyInstance": "123.456.78.910:39898:qGKqCo:Jb26Xz",
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`saveSettings` | **boolean** | Флаг что настройки сохранены

### Пример тела ответа {#response-example-body}

```json
{
    "saveSettings": true
}
```

### Ошибки SetSettings {#errors}

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setSettings/{{apiTokenInstance}}"

payload = "{\r\n\t\"countryInstance\": \"uk\",\r\n\t\"webhookUrl\": \"https://mysite.ru\",\r\n\t\"delaySendMessagesMilliseconds\": 1000,\r\n\t\"markIncomingMessagesReaded\": \"no\",\r\n\t\"proxyInstance\": \"123.456.78.910:39898:qGKqCo:Jb26Xz\",\r\n\t\"outgoingWebhook\": \"yes\",\r\n\t\"stateWebhook\": \"yes\",\r\n\t\"incomingWebhook\": \"yes\",\r\n\t\"deviceWebhook\": \"no\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```