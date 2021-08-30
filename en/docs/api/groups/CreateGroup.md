# CreateGroup

Метод предназначен для создания группового чата.

## Запрос {#request}

Для создания группового чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/CreateGroup/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupName` | **string** | Да | Наименование нового группового чата
`chatIds` | **array<string>** | Да | Коллекция [идентификаторов](../chat-id.md#corr) участников группы

### Пример тела запроса {#request-example-body}

```json
{
    "groupName": "Group created by Green API",
    "chatIds": [
        "79001234568@c.us",
        "79001234569@c.us"
    ]
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`created` | **boolean** | Флаг создания группы
`chatId` | **string** | [Идентификатор группового чата](../chat-id.md#gus)
`groupInviteLink` | **string** | Ссылка приглашения в группу

### Пример тела ответа {#response-example-body}

```json
{
    "created": true,
    "chatId": "79001234567-1587570015@g.us",
    "groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### Ошибки CreateGroup {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/createGroup/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupName\": \"Group created by Green API\",\r\n    \"chatIds\": [\r\n        \"79001234567@c.us\",\r\n        \"79001234568@c.us\"\r\n    ]\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```