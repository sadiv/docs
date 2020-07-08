# ReadChat

Метод предназначен для отметки сообщений в чате прочитанными. Могут быть отмечены прочитанными все сообщения в чате или только одно заданное сообщение.

## Запрос {#request}

Для отметки сообщений в чате прочитанными требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/ReadChat/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](../chat-id)
`idMessage` | **string** | Нет | Идентификатор входящего сообщения, которое необходимо отметить прочитанным. Если не указан, то все непрочитанные сообщения в чате будут отмечены прочитанными.

### Пример тела запроса {#request-example-body}

Отметка прочтения одного сообщения в чате:
```json
{
    "chatId": "79001234567@c.us",
    "idMessage": "B275A7AA0D6EF89BB9245169BDF174E6"
}
```

Отметка прочтения всех сообщений в чате:
```json
{
    "chatId": "79001234567@c.us"
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

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/readChat/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"idMessage\": \"B275A7AA0D6EF89BB9245169BDF174E6\"\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```