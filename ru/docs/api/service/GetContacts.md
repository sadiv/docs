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

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getContacts/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```