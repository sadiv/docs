# ExtendedTextMessage

Получено входящее сообщение о ссылке с данными

## webhook {#webhook}

### Поля webhook {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | Тип webhook уведомления. Возможные варианты stateInstanceChanged, outgoingMessageStatus, incomingMessageReceived, deviceInfo. В данном случае поле равняется incomingMessageReceived.
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX формате
`idMessage` | **string** | Идентификатор входящего сообщения
`senderData` | **object** | Данные об отправителе сообщения/файла
`messageData` | **object** | Данные о принятом сообщении/файле

Поля объекта instanceData

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате Whatsapp
`typeInstance` | **string** | Тип мессенджера для аккаунта

Поля объекта senderData

Параметр | Тип | Описание
----- | ----- | -----
`chatId` | **string** | Идентификатор чата, в котором получено сообщение/файл
`sender` | **string** | Идентификатор отправителя сообщения/файла
`senderName` | **string** | Имя отправителя

Поля объекта messageData

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения, возможные значения: textMessage, imageMessage, videoMessage, documentMessage, audioMessage, locationMessage, contactMessage, extendedTextMessage. В данном случае поле принимает значение extendedTextMessage
`extendedTextMessageData` | **object** | Объект данных о принятой ссылке с метаданными, когда typeMessage = extendedTextMessage

Поля объекта extendedTextMessageData

Параметр | Тип | Описание
----- | ----- | -----
`text` | **string** | Текст ссылки
`description` | **string** | Описание ссылки
`title` | **string** | Заголовок ссылки
`previewType` | **string** | Тип превью ссылки
`jpegThumbnail` | **string** | Превью изображения в base64 кодировке

### Пример тела webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "79001234568@c.us",
        "sender": "79001234568@c.us",
        "senderName": "МТС Мой"
    },
    "messageData": {
        "typeMessage": "extendedTextMessage",
        "extendedTextMessageData": {
            "text": "https://www.youtube.com/xxxxxxxxxxxxxxxxxxx",
            "description": "Друзья! Это новый проект на канале Чердак. Вы увидите как я купил Ford Mustang по цене Iphone. Я начинаю строить настоящий американский Muscle Car. Сейчас у ...",
            "title": "Как купить Ford Mustang по цене Iphone XS",
            "previewType": "video",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFxQYG=="
        }
    }
}
```
