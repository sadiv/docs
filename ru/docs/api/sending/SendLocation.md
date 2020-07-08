# SendLocation

Метод предназначен для отправки сообщения геолокации.
Сообщение будет добавлено в очередь на отправку.
Скорость отправки сообщений из очереди регулирует параметр [Интервал отправки сообщений](/api/send-messages-delay).

## Запрос {#request}

Для отправки сообщения геолокации требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendLocation/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](/api/chat-id)
`nameLocation` | **string** | Нет | Название локации
`address` | **string** | Нет | Адрес локации
`latitude` | **double** | Да | Широта локации
`longitude` | **double** | Да | Долгота локации

### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "chatId": "79001234567@c.us",
    "nameLocation": "Restaurant",
    "address": "123456, Perm",
    "latitude": 12.3456789,
    "longitude": 10.1112131
}
```

Отправка сообщения в групповой чат:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "nameLocation": "Restaurant",
    "address": "123456, Perm",
    "latitude": 12.3456789,
    "longitude": 10.1112131
}
```
## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | -----
`idMessage ` | **string** | Идентификатор отправленного сообщения 

### Пример тела ответа {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Ошибки SendLocation {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLocation/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567@c.us\",\r\n    \"nameLocation\": \"Я здесь, приезжай\",\r\n    \"address\": \"613123, Perm\",\r\n   \t\"latitude\": 44.9370129,\r\n    \"longitude\": 89.8728409\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```