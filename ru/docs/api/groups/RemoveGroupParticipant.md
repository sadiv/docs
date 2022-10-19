# RemoveGroupParticipant

Метод удаляет участника из группового чата.

## Запрос {#request}

Для удаления участника из группового чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/RemoveGroupParticipant/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | [Идентификатор группового чата](../chat-id.md#gus)
`participantChatId` | **string** | Да | [Идентификатор](../chat-id.md#corr) участника, удаляемого из группы

### Пример тела запроса {#request-example-body}

Удаление участника группового чата:
```json
{
    "groupId": "120363043968066561@g.us",
    "participantChatId": "79001234565@c.us"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`removeParticipant` | **boolean** | Флаг удаления участника из группы

### Пример тела ответа {#response-example-body}

```json
{
    "removeParticipant": true
}
```

### Ошибки RemoveGroupParticipant {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/removeGroupParticipant/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"120363043968066561@g.us\",\r\n    \"participantChatId\": \"79001234568@c.us\",\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```