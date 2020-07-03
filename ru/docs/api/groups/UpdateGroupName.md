# UpdateGroupName

Метод изменяет название группы Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | Идентификатор группы
`groupName` | **string** | Да | Название группы

### Пример тела запроса {#request-example-body}

```json
{
    "groupId": "12345678910-1112131415@g.us",
    "groupName":"Changed name by API"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`updateGroupName` | **boolean** | Флаг изменения названия группы

### Пример тела ответа {#response-example-body}

```json
{
    "updateGroupName": true
}
```

### Ошибки UpdateGroupName {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/updateGroupName/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"12345678910-1112131415@g.us\",\r\n    \"groupName\":\"Changed name by API\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```