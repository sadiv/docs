# ReadChatMessage

Метод предназначен для отметки входящего сообщения прочитанным

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Если не указан `phoneNumber` | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`phoneNumber` | **integer** | Если не указан `chatId` | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`
`idMessage` | **string** | Нет | Идентификатор входящего сообщения, который необходимо отметить прочитанным. Если не указан, то все непрочитанные входящие сообщения в чате будут отмечены прочитанными

### Пример тела запроса {#request-example-body}

Чтение сообщений по id:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "idMessage": "B275A7AA0D6EF89BB9245169BDF174E6"
}
```

Чтение сообщений по номеру телефона:
```json
{
    "phoneNumber": 79001234567,
    "idMessage": "B275A7AA0D6EF89BB9245169BDF174E6"
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

### Ошибки ReadChatMessage {#errors}

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/readChat/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567-1581234048@g.us\",\r\n    \"idMessage\": \"B275A7AA0D6EF89BB9245169BDF174E6\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```