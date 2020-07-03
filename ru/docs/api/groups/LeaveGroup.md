# LeaveGroup

Метод производит выход пользователя из группы

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | Идентификатор группы

### Пример тела запроса {#request-example-body}

```json
{
    "groupId": "79001234567-1587570015@g.us"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`leaveGroup` | **boolean** | Флаг выхода из группы

### Пример тела ответа {#response-example-body}

```json
{
    "leaveGroup": true
}
```

### Ошибки LeaveGroup {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/leaveGroup/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"79001234567-1587570015@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```