# AddGroupParticipant

Метод добавляет участника в групповой чат.

## Запрос {#request}

Для добавления участника в групповой чат требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/AddGroupParticipant/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | [Идентификатор группового чата](../chat-id.md#gus)
`participantChatId` | **string** | Да | [Идентификатор](../chat-id.md#corr) участника, добавляемого в групповой чат.

### Пример тела запроса {#request-example-body}

Добавление участника в групповой чат:
```json
{
    "groupId": "79001234567-1587570015@g.us",
    "participantChatId": "79001234568@c.us"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`addParticipant` | **boolean** | Флаг добавления участника в групповой чат

### Пример тела ответа {#response-example-body}

```json
{
    "addParticipant": true
}
```

### Ошибки AddGroupParticipant {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/addGroupParticipant/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"79001234567-1581234048@g.us\",\r\n\t\"participantChatId\": \"79001234568@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```