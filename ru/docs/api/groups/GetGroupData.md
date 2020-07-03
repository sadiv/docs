# GetGroupData

Метод получает данные о группе Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | Идентификатор группы

### Пример тела запроса {#request-example-body}

```json
{
    "groupId": "12345678910-1112131415@g.us"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`groupId` | **string** | Идентификатор группы
`owner` | **string** | Владелец группы
`subject` | **string** | Тема (название) группы
`creation` | **integer** | Время создания группы в Unix
`participants` | **array** | Коллекция участников группы
`subjectTime` | **integer** | Время создание темы (названия) группы в Unix
`subjectOwner` | **string** | Идентификатор пользователя создавшего тему группы
`groupInviteLink` | **string** | Ссылка приглашения в группу

Поля объектов из массива participants

Поле | Тип |  Описание
----- | ----- | ----- 
`id` | **string** | Идентификатор пользователя
`isAdmin` | **boolean** | Флаг является ли пользователь администратором группы
`isSuperAdmin` | **boolean** | Флаг является ли пользователь супер администратором группы

### Пример тела ответа {#response-example-body}

```json
{
	"groupId": "12345678910-1112131415@g.us",
	"owner": "12345678910@c.us",
	"subject": "Changed name by API",
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
	"subjectOwner": "12345678910@c.us",
	"groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### Ошибки GetGroupData {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getGroupData/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"12345678910-1112131415@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```