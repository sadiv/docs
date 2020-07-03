# GetContacts

Метод предназначен для получения списка контактов аккаунта Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Отсутствуют

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`id` | **string** | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`name` | **string** | Имя контакта
`type` | **string** | Тип контакта, возможные значения user/group

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

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getContacts/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```