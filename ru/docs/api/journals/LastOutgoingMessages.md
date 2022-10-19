# LastOutgoingMessages

Метод возвращает крайние отправленные сообщения аккаунта. По умолчанию возвращаются последние сообщения за 24 часа.

## Запрос {#request}

Для получения отправленных сообщений требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/LastOutgoingMessages/{{apiTokenInstance}}?minutes={{minutes_count}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры URL запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`minutes` | **integer** | нет | время в минутах, за которое требуется показать сообщения (по умолчанию равно 1440 минут)


## Ответ {#response}

### Поля ответа {#response-parameters}

Массив объектов с полями:

Поле | Тип |  Описание
----- | ----- | ----- 
`idMessage` | **string** | Идентификатор исходящего сообщения
`timestamp` | **integer** | Время крайнего действия по сообщению в UNIX-формате
`statusMessage` | **string** | Статус исходящего сообщения, возможные значения:
| | `noAccount` - нет аккаунта WhatsApp на номере телефона
| | `notInGroup` - не состоите в данной группе
| | `pending` - сообщение отправляется
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
`chatId` | **string** | [Идентификатор чата](../chat-id.md), в который сообщение было отправлено
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
        "idMessage": "3EB0BDDC94BFDFB3D4FA",
        "timestamp": 1587133830,
        "statusMessage": "read",
        "typeMessage": "textMessage",
        "chatId": "79001234567@c.us",
        "textMessage": "Привет",
    },
    {
        "idMessage": "3EB0BDDC94BFDFB3D4FA",
        "timestamp": 1587133830,
        "statusMessage": "read",
        "typeMessage": "imageMessage",
        "chatId": "79001234567@c.us",
        "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/3EB0BDDC94BFDFB3D4FA",
        "caption": "Как тебе?"
    }
]
```

### Ошибки LastOutgoingMessages {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/lastOutgoingMessages/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```