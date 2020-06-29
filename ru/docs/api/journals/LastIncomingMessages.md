# LastIncomingMessages

Метод возвращает крайние входящие сообщения аккаунта Whatsapp.
Срок хранения входящих сообщений на сервере равен 24 часа.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Отсутствуют

## Ответ {#response}

### Поля ответа {#response-parameters}

Массив объектов с полями:

Поле | Тип |  Описание
----- | ----- | ----- 
`idMessage` | **string** | Идентификатор входящего сообщения
`timestamp` | **integer** | Время принятия сообщения в UNIX
`typeMessage` | **string** | Тип сообщения, возможные значения:
| | textMessage - текстовое сообщение
| | imageMessage - сообщение с изображением
| | videoMessage - видео сообщение
| | documentMessage - сообщение с файлом документа
| | audioMessage - аудио сообщение
| | locationMessage - сообщение геолокации
| | contactMessage - сообщение с контактом
| | extendedTextMessage - сообщение со ссылкой и превью
`chatId` | **string** | Идентификатор чата в котором получено сообщение
`senderName` | **string** | Имя отправителя сообщения
`textMessage` | **string** | Текст сообщения, если typeMessage=textMessage
`downloadUrl` | **string** | Ссылка на скачивание файла, если typeMessage = imageMessage/videoMessage/documentMessage/audioMessage
`caption` | **string** | Описание файла
`location` | **object** | Объект о структуре локации
`contact` | **object** | Объект о структуре контакта
`extendedTextMessage` | **object** | Объект о структуре данных ссылки

Поля объекта location:

Поле | Тип |  Описание
----- | ----- | ----- 
`nameLocation` | **string** | Название локации
`address` | **string** | Адрес локации
`latitude` | **double** | Широта локации
`longitude` | **double** | Долгота локации
`jpegThumbnail` | **string** | Превью изображения в base64 кодировке

Поля объекта contact:

Поле | Тип |  Описание
----- | ----- | ----- 
`displayName` | **string** | Отображаемое имя контакта
`vcard` | **string** | Структура VCard (визитной карточки контакта)

Поля объекта extendedTextMessage:

Поле | Тип |  Описание
----- | ----- | ----- 
`text` | **string** | Текст ссылки
`description` | **string** | Описание ссылки
`title` | **string** | Заголовок ссылки
`previewType` | **string** | Тип превью ссылки
`jpegThumbnail` | **string** | Превью изображения в base64 кодировке

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
        "downloadUrl": "https://wapi.apisender.com/waInstance1/downloadFile/EA0BD1AE042DC4F3609867126309D67C",
        "caption": "Как тебе?"
    }
]
```

### Ошибки LastIncomingMessages {#errors}

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/lastIncomingMessages/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```