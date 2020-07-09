# GetAvatar

Метод возвращает аватар корреспондента или группового чата.

## Запрос {#request}

Для получения аватара требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetAvatar/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор корреспондента или группового чата](../chat-id.md)

### Пример тела запроса {#request-example-body}

Получить аватар корреспондента:
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
`existsWhatsapp` | **boolean** | Флаг наличия учетной записи WhatsApp на номере телефона корреспондента
`urlAvatar` | **string** | Ссылка на аватар корреспондента или группового чата. Параметр принимает пустое значение в случае, если аватар не установлен или у корреспондента нет учетной записи WhatsApp (`existsWhatsapp`=`false`)
`reason` | **string** | Причина почему аватар не был проверен. Присутствует когда не удалось выполнить проверку, возможные значения:
| | `bad request data` - Неверный формат номера телефона. Номер телефона должен содержать 11 или 12 цифр. Или идентификатора чата
| | `get avatar timeout limit exceeded` - Превышен лимит времени ожидания ответа о наличии аватара

### Пример тела ответа {#response-example-body}

```json
{
  	"existsWhatsapp": true,
 	  "urlAvatar": "https://pps.whatsapp.net/v/link/to/the/image"
}
```

### Ошибки GetAvatar {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
200|`bad request data`| Неверный формат номера телефона. Номер телефона должен содержать 11 или 12 цифр. Или идентификатора чата
200|`get avatar timeout limit exceeded`| Превышен лимит времени ожидания ответа о наличии аватара

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