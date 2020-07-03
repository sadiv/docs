# GetAvatar

Метод возвращает аватар аккаунта Whatsapp или группового чата.

## Запрос {#request}

Для получения аватара требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetAvatar/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](/before-start#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](/api/chat-id)

### Пример тела запроса {#request-example-body}

Получить аватар аккаунта Whatsapp:
```json
{
    "chatId": "79001234567@c.us"
}
```

Получить аватар группового чата:
```json
{
    "chatId": "79001234567-1581234048@g.us"
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

payload = "{\r\n    \"chatId\": \"79001234567@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```