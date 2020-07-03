# CreateGroup

Метод предназначен для создания группы Whatsapp.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupName` | **string** | Да | Название группы
`chatIds` | **array<string>** | Если не указано поле phones | Коллекция идентификаторов участников группы
`phones` | **array<integer>** | Если не указано поле chatIds | Коллекция номеров телефонов участников группы

### Пример тела запроса {#request-example-body}

```json
{
    "groupName": "From API Group created",
    "chatIds": [],
    "phones": [
        79001234567,
        79001234568
    ]
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`created` | **boolean** | Флаг создания группы
`chatId` | **string** | [Идентификатор чата](/api/chat-id)
`groupInviteLink` | **string** | Ссылка приглашения в группу

### Пример тела ответа {#response-example-body}

```json
{
    "created": true,
    "chatId": "12345678910-1112131415@g.us",
    "groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### Ошибки CreateGroup {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/createGroup/{{apiTokenInstance}}"

payload = "{\r\n    \"groupName\": \"From API Group created\",\r\n    \"chatIds\": [],\r\n    \"phones\": [\r\n        79001234567,\r\n        79001234568\r\n    ]\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```