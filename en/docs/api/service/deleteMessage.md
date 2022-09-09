# deleteMessage
Метод удаляет сообщение из чата.
## Запрос {#request}

Для удаления сообщения из чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/deleteMessage/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор корреспондента или группового чата](../chat-id.md)
`idMessage` | **string** | Да | ID удаляемого сообщения

### Пример тела запроса {#request-example-body}

```json
{
    "chatId": "120363043968066561@g.us",
    "idMessage": "BAE5F4886F6F2D05"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Тело ответа пустое. При успехе ответ сервера 200.

### Ошибки deleteMessage {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `chatId not found` | chatID не найдено
400 | `ID message notfound` | IDMessage не найдено

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/deleteMessage/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"120363043968066561@g.us\, \"idMessage\": \"BAE5F4886F6F2D05\" \"r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```