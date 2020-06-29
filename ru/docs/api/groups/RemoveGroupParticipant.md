# RemoveGroupParticipant

Метод удаляет участника из группы Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | Идентификатор группы
`participantChatId` | **string** | Если не указан participantPhone | Идентификатор участника, удаляемого из группы
`participantPhone` | **integer** | Если не указан participantChatId | Номер телефона участника, удаляемого из группы

### Пример тела запроса {#request-example-body}

Удаление по id:
```json
{
    "groupId": "79001234567-1587570015@g.us",
    "participantChatId": "79001234568-1112131415@g.us",
}
```

Удаление по телефону:
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
`removeParticipant` | **boolean** | Флаг удаления участника из группы

### Пример тела ответа {#response-example-body}

```json
{
    "removeParticipant": true
}
```

### Ошибки RemoveGroupParticipant {#errors}

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/removeGroupParticipant/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"79001234567-1587570015@g.us\",\r\n    \"participantChatId\": \"79001234568-1112131415@g.us\",\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```