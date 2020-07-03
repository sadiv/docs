# AddGroupParticipant

Метод добавляет участника в группу Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | Идентификатор группы
`participantChatId` | **string** | Если не указан participantPhone | Идентификатор участника, добавляемого в группу
`participantPhone` | **integer** | Если не указан participantChatId | Номер телефона участника, добавляемого в группу

### Пример тела запроса {#request-example-body}

Добавление по id:
```json
{
    "groupId": "79001234567-1587570015@g.us",
    "participantChatId": "79001234568-1112131415@g.us",
}
```

Добавление по телефону:
```json
{
    "groupId": "79001234567-1587570015@g.us",
    "participantPhone": 79001234568
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`addParticipant` | **boolean** | Флаг добавления участника в группу

### Пример тела ответа {#response-example-body}

```json
{
    "addParticipant": true
}
```

### Ошибки AddGroupParticipant {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/addGroupParticipant/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"79001234567-1581234048@g.us\",\r\n\t\"participantPhone\": 79001234568\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```