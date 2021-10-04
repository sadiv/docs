# GetAvatarAsync

Метод возвращает аватар корреспондента или группового чата асинхронно. В отличие от метода [GetAvatar](GetAvatar) результат запроса возвращается в виде вебхука AvatarInfo

## Запрос {#request}

Для получения аватара требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetAvatarAsync/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор корреспондента или группового чата](../chat-id.md)

### Пример тела запроса {#request-example-body}

Для получения своего аватара - укажите в chatId свой номер ("{ваш номер}@c.us").

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

Успешный запрос возвращает пустой ответ со статусом 200

### Ошибки GetAvatar {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
200|`bad request data`| Неверный формат номера телефона. Номер телефона должен содержать 11 или 12 цифр. Или идентификатора чата

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getAvatarAsync/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

requests.request("POST", url, headers=headers, data = payload)

```