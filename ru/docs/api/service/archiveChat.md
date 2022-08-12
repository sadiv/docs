# ArchiveChat
Метод архивирует чат. Архивировать можно чаты, в которых есть хотя бы одно входящее сообщение.
## Запрос {#request}

Для архивации чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/archiveChat/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор корреспондента или группового чата](../chat-id.md)

### Пример тела запроса {#request-example-body}

```json
{
    "chatId": "120363043968066561@g.us"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Тело ответа пустое. При успехе ответ сервера 200.

### Ошибки archiveChat {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `"ArchiveChatError: cannot archive chat cause last message not found in chat"` | chatID не верно или в чате нет сообщений

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/archiveChat/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"120363043968066561@g.us\"r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```