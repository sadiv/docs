# LeaveGroup

Метод производит выход пользователя текущего аккаунта из группового чата.

## Запрос {#request}

Для выхода из группового чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/LeaveGroup/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | [Идентификатор группового чата](../chat-id.md#gus), из которого необходимо выйти.

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

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

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