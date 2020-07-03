# GetAvatar

Метод возвращает аватар аккаунта Whatsapp или группы

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Если не указан `phoneNumber` | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`phoneNumber` | **integer** | Если не указан `chatId` | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`

### Пример тела запроса {#request-example-body}

Узнать аватар по id:
```json
{
    "chatId": "79001234567-1581234048@g.us"
}
```

Узнать аватар по телефону:
```json
{
    "phoneNumber": 79001234567
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`existsWhatsapp` | **boolean** | Флаг наличия Whatsapp на номере телефона
`urlAvatar` | **string** | Ссылка на аватар пользователя/группы, пустое значение когда аватара нет или existsWhatsapp=false
`reason` | **string** | Причина почему аватар не был проверен, присутствует когда не удалось выполнить проверку, возможные значения:
| | bad request data - неверный формат номера телефона, должен быть 11 или 12 цифр. Или идентификатора чата;
| | get avatar timeout limit exceeded - превышен лимит времени ожидания ответа о наличии аватара;

### Пример тела ответа {#response-example-body}

```json
{
  	"existsWhatsapp": true,
 	"urlAvatar": "https://pps.whatsapp.net/v/link/to/the/image",
	"reason": ""
}
```

### Ошибки GetAvatar {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getAvatar/{{apiTokenInstance}}"

payload = "{\r\n    \"phoneNumber\": 79001234567\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```