# GetGroupData

Метод получает данные группового чата.

## Запрос {#request}

Для получения данных группового чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetGroupData/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | [Идентификатор группового чата](../chat-id.md#gus)

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
`groupId` | **string** | [Идентификатор группового чата](../chat-id.md#gus)
`owner` | **string** | [Идентификатор](../chat-id.md#corr) владельца группы
`subject` | **string** | Наименование группы
`creation` | **integer** | Время создания группы в Unix-формате
`participants` | **array** | Коллекция участников группы
`subjectTime` | **integer** | Время создания наименования группы в Unix-формате
`subjectOwner` | **string** | [Идентификатор](../chat-id.md#corr) пользователя создавшего наименование группы
`groupInviteLink` | **string** | Ссылка приглашения в группу

Поля объектов из массива `participants`

Поле | Тип |  Описание
----- | ----- | ----- 
`id` | **string** | [Идентификатор](../chat-id.md#corr) участника группового чата
`isAdmin` | **boolean** | Флаг, является ли пользователь администратором группы
`isSuperAdmin` | **boolean** | Флаг, является ли пользователь супер администратором группы

### Пример тела ответа {#response-example-body}

```json
{
	"groupId": "79001234567-1587570015@g.us",
	"owner": "79001234567@c.us",
	"subject": "Green API Group",
	"creation": 1587570015,
	"participants": [
		{
			"id": "79001234567@c.us",
			"isAdmin": true,
			"isSuperAdmin": true
		},
		{
			"id": "79001234568@c.us",
			"isAdmin": true,
			"isSuperAdmin": false
		},
		{
			"id": "79001234569@c.us",
			"isAdmin": false,
			"isSuperAdmin": false
		}
	],
	"subjectTime": 1587737715,
	"subjectOwner": "79001234567@c.us",
	"groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### Ошибки GetGroupData {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getGroupData/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"79001234567-1587570015@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```