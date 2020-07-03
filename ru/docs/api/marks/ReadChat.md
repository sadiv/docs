# ReadChat

Метод предназначен для отметки входящих сообщений в чате прочитанными

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Если не указан `phoneNumber` | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`phoneNumber` | **integer** | Если не указан `chatId` | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`

### Пример тела запроса {#request-example-body}

Чтение сообщений по id:
```json
{
    "chatId": "79001234567-1581234048@g.us",
}
```

Чтение сообщений по номеру телефона:
```json
{
    "phoneNumber": 79001234567,
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`setRead` | **boolean** | Флаг отметки сообщений прочитанными

### Пример тела ответа {#response-example-body}

```json
{
    "setRead": true
}
```

### Ошибки ReadChat {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/readChat/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567-1581234048@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```