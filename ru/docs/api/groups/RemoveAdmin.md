# RemoveAdmin

Метод лишает участника прав администрирования группового чата.

## Запрос {#request}

Для лишения участника прав администрирования группового чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/RemoveAdmin/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](/before-start#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | [Идентификатор группового чата](/api/chat-id#gus)
`participantChatId` | **string** | Да | [Идентификатор](/api/chat-id#corr) участника группы, которого требуется лишить прав администрирования группы

### Пример тела запроса {#request-example-body}

Лишение участника прав администрирования группы:
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
`removeAdmin` | **boolean** | Флаг лишения участника группы прав администратора

### Пример тела ответа {#response-example-body}

```json
{
    "removeAdmin": true
}
```

### Ошибки RemoveAdmin {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/removeAdmin/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"79001234567-1587570015@g.us\",\r\n    \"participantChatId\": \"79001234568@c.us\",\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
