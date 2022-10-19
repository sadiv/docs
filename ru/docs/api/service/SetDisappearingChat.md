# Set Disappearing Chat

Метод предназначен для изменения настроек исчезающих сообщений в чатах. Используются стандартные настройки приложения: 0 (выключено), 86400 (24 часа), 604800 (7 дней), 7776000 (90 дней).

## Запрос {#request}

Для установки настроек требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/setDisappearingChat/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор корреспондента](../chat-id.md)
`ephemeralExpiration` | **integer** | Нет | Время жизни сообщений в секундах, принимает значения: 0, 86400, 604800, 7776000

### Пример тела запроса {#request-example-body}

```json
{
    "chatId": "71234567890@c.us",
    "ephemeralExpiration": 0
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`chatId` | **string** | Да | [Идентификатор корреспондента](../chat-id.md)
`disappearingMessagesInChat` | **boolean** | Состояние чата (исчезающий или обычный) принимает значения: true, false
`ephemeralExpiration` | **integer** | Время жизни сообщений в чате, принимает значения в секундах: 0, 86400, 604800, 7776000


### Пример тела ответа {#response-example-body}

```json
{
    "chatId": "712345678910@c.us",
    "disappearingMessagesInChat": false,
    "ephemeralExpiration": 0
}
```

### Ошибки SetDisappearingChat {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```

import requests
import json

url = "https://api.green-api.com/waInstance{{idInstance}}/setDisappearingChat/{{apiTokenInstance}}
"
payload = json.dumps({
  "chatId": "712345678910@c.us",
  "ephemeralExpiration": 0
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```