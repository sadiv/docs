# SendLocation

Метод предназначен для отправки сообщения геолокации.
Сообщение будет добавлено в очередь на отправку.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Если не указан `phoneNumber` | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`phoneNumber` | **integer** | Если не указан `chatId` | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`
`nameLocation` | **string** | Нет | Название локации
`address` | **string** | Нет | Адрес локации
`latitude` | **double** | Да | Широта локации
`longitude` | **double** | Да | Долгота локации

### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "phoneNumber": 79001234567,
    "nameLocation": "Restaurant",
    "address": "123456, Perm",
    "latitude": 12.3456789,
    "longitude": 10.1112131
}
```

Отправка сообщения в группу:
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

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLocation/{{apiTokenInstance}}"

payload = "{\r\n    \"phoneNumber\": 79001234567,\r\n    \"nameLocation\": \"Restaurant\",\r\n    \"address\": \"123456, Perm\",\r\n   \t\"latitude\": 12.3456789,\r\n    \"longitude\": 10.1112131\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```