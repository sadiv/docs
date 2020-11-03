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
`chatId` | **string** | Да | [Идентификатор чата](../chat-id.md)

`textMessage` | **string** | ХХХ
`downloadUrl` | **string** | ХХХ

`senderId` | **string** | ХХХ
`senderName` | **string** | ХХХ



`idMessage` | **string** | Идентификатор входящего сообщения
`timestamp` | **integer** | Время принятия сообщения в UNIX-формате
`typeMessage` | **string** | Тип сообщения, возможные значения:
| | `textMessage` - текстовое сообщение
| | `imageMessage` - сообщение с изображением
| | `videoMessage` - видео сообщение
| | `documentMessage` - сообщение с файлом документа
| | `audioMessage` - аудио сообщение
| | `locationMessage` - сообщение геолокации
| | `contactMessage` - сообщение с контактом
| | `extendedTextMessage` - сообщение со ссылкой и превью
`chatId` | **string** | [Идентификатор чата](../chat-id.md), в котором получено сообщение
`senderId` | **string** | [Идентификатор](../chat-id.md#corr) отправителя сообщения
`senderName` | **string** | Имя отправителя сообщения
`textMessage` | **string** | Текст сообщения, если `typeMessage`=`textMessage`
`downloadUrl` | **string** | Ссылка на скачивание файла, если `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`/`audioMessage`
`caption` | **string** | Описание файла
`location` | **object** | Объект о структуре локации
`contact` | **object** | Объект о структуре контакта
`extendedTextMessage` | **object** | Объект о структуре данных ссылки

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
        "idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
        "timestamp": 1587129319,
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Николай",
        "textMessage": "Привет"
    },
    {
        "idMessage": "EA0BD1AE042DC4F3609867126309D67C",
        "timestamp": 1587147598,
        "typeMessage": "imageMessage",
        "chatId": "79001234567@c.us",
        "senderId": "79001234567@c.us",
        "senderName": "Николай",
        "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/EA1BD1AE042DC4F3609867126309D67C",
        "caption": "Как тебе?"
    }
]
```

### Ошибки LastIncomingMessages {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/lastIncomingMessages/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```