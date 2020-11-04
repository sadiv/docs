# GetChatHistory

Метод возвращает историю сообщений чата.

> **Важно:** История сообщений хранится и извлекается из телефонного аппарата, поэтому важно, чтобы телефон был доступен. В случае, если телефон потеряет связь, вызов метода может завешиться ошибкой HTTP `504`.

## Запрос {#request}

Для получения истории сообщений требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetChatHistory/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор личного или группового чата](../chat-id.md) историю сообщений которого требуется получить
`count ` | **integer** | Нет | Количество сообщений для получения. Значение по умолчанию `100`  

### Пример тела запроса {#request-example-body}

Запрос последних 10 сообщений:
```json
{
    "chatId": "79001234567@c.us",
    "count": 10
}
```

## Ответ {#response}

Ответ содержит список всех полученных и отправленных сообщений в чате. Сортировка по убыванию даты отправки сообщения.

### Поля ответа {#response-parameters}

Массив объектов с полями:

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | Вид сообщения: `outgoing` - исходящее сообщение; `incoming` - входящее сообщение
`timestamp` | **integer** | Время отправки сообщения в UNIX-формате
`idMessage` | **string** | Идентификатор сообщения
`statusMessage` | **string** | Статус исходящего сообщения. Присутствует только для `type` = `outgoing`. Возможные значения:
| | `sent` - отправлено
| | `delivered` - доставлено
| | `read` - прочитано/просмотрено/прослушано
`typeMessage` | **string** | Тип сообщения, возможные значения:
| | `textMessage` - текстовое сообщение
| | `imageMessage` - сообщение с изображением
| | `videoMessage` - видео сообщение
| | `documentMessage` - сообщение с файлом документа
| | `audioMessage` - аудио сообщение
| | `locationMessage` - сообщение геолокации
| | `contactMessage` - сообщение с контактом
| | `extendedTextMessage` - сообщение со ссылкой и превью
`chatId` | **string** | [Идентификатор чата](../chat-id.md)
`senderId` | **string** | [Идентификатор](../chat-id.md#corr) отправителя сообщения входящего сообщения. Присутствует только для `type` = `incoming`
`senderName` | **string** | Имя отправителя входящего сообщения. Присутствует только для `type` = `incoming`
`textMessage` | **string** | Текст сообщения, если `typeMessage`=`textMessage`
`downloadUrl` | **string** | Ссылка на скачивание файла, если `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`/`audioMessage`
`caption` | **string** | Описание файла, если `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`
`location` | **object** | Объект о структуре локации, если `typeMessage`=`locationMessage`
`contact` | **object** | Объект о структуре контакта, если `typeMessage`=`contactMessage`
`extendedTextMessage` | **object** | Объект о структуре данных ссылки, если `typeMessage`=`extendedTextMessage`

Поля объекта `location`:

Поле | Тип |  Описание
----- | ----- | ----- 
`nameLocation` | **string** | Название локации
`address` | **string** | Адрес локации
`latitude` | **double** | Широта локации
`longitude` | **double** | Долгота локации
`jpegThumbnail` | **string** | Превью изображения в `base64` кодировке

Поля объекта `contact`:

Поле | Тип |  Описание
----- | ----- | ----- 
`displayName` | **string** | Отображаемое имя контакта
`vcard` | **string** | Структура VCard (визитной карточки контакта)

Поля объекта `extendedTextMessage`:

Поле | Тип |  Описание
----- | ----- | ----- 
`text` | **string** | Текст ссылки
`description` | **string** | Описание ссылки
`title` | **string** | Заголовок ссылки
`previewType` | **string** | Тип превью ссылки
`jpegThumbnail` | **string** | Превью изображения в `base64` кодировке

### Пример тела ответа {#response-example-body}

```json
[
    {
        "type": "incoming",
        "timestamp": 1603964449,
        "idMessage": "3AADDD555CB0822C0539",
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Andrew Sh",
        "textMessage": "I use Green-API to get this message from you!"
    },
    {
        "type": "outgoing",
        "timestamp": 1604316706,
        "idMessage": "3EB08816FEBCCC3FACD2",
        "statusMessage": "read",
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "textMessage": "I use Green-API to send this message to you!"
    },
    {
        "type": "incoming",
        "timestamp": 1604466117,
        "idMessage": "3AA45F9F285C5249CDFC",
        "typeMessage": "imageMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Andrew Sh",
        "downloadUrl": "https://api.green-api.com/waInstance9075/downloadFile/download-file-id",
        "caption": "Green API Logo"
    }
]
```

### Ошибки GetChatHistory {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/GetChatHistory/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"count\": 100\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
