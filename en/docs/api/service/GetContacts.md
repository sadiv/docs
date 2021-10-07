# GetContacts

Метод предназначен для получения списка контактов текущего аккаунта.

Присылает контакты всех получателей, с кем была связь на аккаунте.
Поле "имя контакта" 'name' принимает значение исходя из следующих условий:
1) Если аккаунт записан в телефонную книгу, то получаем имя из книги;
2) Если аккаунт не записан в телефонную книгу, то получаем имя из профиля WhatsApp;
3) Если аккаунт не записан в телефонную книгу и не назначено имя профиля в WhatsApp, то получаем пустое поле.

## Request {#request}

Для получения списка контактов требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetContacts/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`id` | **string** | [Идентификатор корреспондента или группового чата](../chat-id.md)
`name` | **string** | Contact name
`type` | **string** | Тип контакта. Возможные значения:
||`user` - контакт приналдежит корреспонденту
||`group` - контакт является групповым чатом


### Response body example {#response-example-body}

```json
[
    {
        "id": "79001234567@c.us",
        "name": "Ivan Petrov",
        "type": "user"
    },
    {
        "id": "79001234568@c.us",
        "name": "Lyusya Sidorova",
        "type": "user"
    },
    {
        "id": "79001234569-1479621234@g.us",
        "name": "My group",
        "type": "group"
    }
]
```

### GetContacts errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getContacts/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
