# Входящие сообщения

В данном разделе приводится описание общих полей входящих сообщений webhook с типом `incomingMessageReceived`. Описание всех типов webhook уведолмений представлено в разделе [Типы webhook уведомлений](/api/receiving/webhook/type-webhook).

Система предусматривает получение webhook уведомлений о входящих сообщениях следующих видов:

- [Входящее текстовое сообщение](/api/receiving/webhook/incoming-message/TextMessage)
- [Входящее текстовое сообщение с URL](/api/receiving/webhook/incoming-message/ExtendedTextMessage)
- [Входящее сообщение с изображением, видео, аудио, документом](/api/receiving/webhook/incoming-message/ImageMessage)
- [Входящее сообщение с геолокацией](/api/receiving/webhook/incoming-message/LocationMessage)
- [Входящее сообщение с контактом](/api/receiving/webhook/incoming-message/ContactMessage)

## Поля webhook incomingMessageReceived {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | [Тип webhook уведомления](/api/receiving/webhook/type-webhook). Для webhook уведомления данного типа поле принимает значение `incomingMessageReceived`
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX-формате
`idMessage` | **string** | Идентификатор входящего сообщения
`senderData` | **object** | Данные об отправителе сообщения или файла
`messageData` | **object** | Данные о принятом сообщении или файле

Поля объекта `instanceData`

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате WhatsApp
`typeInstance` | **string** | Тип мессенджера для аккаунта

Поля объекта `senderData`

Параметр | Тип | Описание
----- | ----- | -----
`chatId` | **string** | [Идентификатор чата](/api/chat-id), в котором получено сообщение или файл
`sender` | **string** | [Идентификатор](/api/chat-id#corr) отправителя сообщения или файла
`senderName` | **string** | Имя отправителя

### Поля объекта `messageData`

Объект `messageData` имеет разные поля в зависимости от типа входящего сообщения:

- [Входящее текстовое сообщение](/api/receiving/webhook/incoming-message/TextMessage)
- [Входящее текстовое сообщение с URL](/api/receiving/webhook/incoming-message/ExtendedTextMessage)
- [Входящее сообщение с изображением, видео, аудио, документом](/api/receiving/webhook/incoming-message/ImageMessage)
- [Входящее сообщение с геолокацией](/api/receiving/webhook/incoming-message/LocationMessage)
- [Входящее сообщение с контактом](/api/receiving/webhook/incoming-message/ContactMessage)

### Пример тела webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "79001234568@c.us",
        "sender": "79001234568@c.us",
        "senderName": "Green API"
    },
    "messageData":{
       ...
       ...
       ...
        }
    }
}
```