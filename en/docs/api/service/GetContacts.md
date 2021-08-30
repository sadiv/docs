# GetContacts

Метод предназначен для получения списка контактов текущего аккаунта.

## Запрос {#request}

Для получения списка контактов требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetContacts/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`id` | **string** | [Идентификатор корреспондента или группового чата](../chat-id.md)
`name` | **string** | Имя контакта
`type` | **string** | Тип контакта. Возможные значения:
||`user` - контакт приналдежит корреспонденту
||`group` - контакт является групповым чатом


### Пример тела ответа {#response-example-body}

```json
[
    {
        "id": "79001234567@c.us",
        "name": "Иван Петров",
        "type": "user"
    },
    {
        "id": "79001234568@c.us",
        "name": "Люся Сидорова",
        "type": "user"
    },
    {
        "id": "79001234569-1479621234@g.us",
        "name": "Моя группа",
        "type": "group"
    }
]
```

### Ошибки GetContacts {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getContacts/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```