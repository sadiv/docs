# Входящие сообщения

Описание общих полей входящих сообщений. Входящие сообщения могут быть следующих типов:

- `textMessage` - текстовое сообщение
- `imageMessage` - сообщение с изображением
- `videoMessage` - видео сообщение
- `documentMessage` - сообщение с файлом документа
- `audioMessage` - аудио сообщение
- `locationMessage` - сообщение геолокации
- `contactMessage` - сообщение с контактом
- `extendedTextMessage` - сообщение со ссылкой и превью

## Webhook {#webhook}

### Поля webhook incomingMessageReceived {#webhook-parameters}

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

#### Поля объекта `messageData`

Объект `messageData` имеет разные поля в зависимости от типа входящего сообщения:

- [Входящее текстовое сообщение](/api/receiving/webhook/incoming-message/TextMessage)
- [Входящее текстовое сообщение с URL](/api/receiving/webhook/incoming-message/ExtendedTextMessage)
- [Входящее сообщение с изображением, видео, аудио, документом](/api/receiving/webhook/incoming-message/ImageMessage)
- [Входящее сообщение с геолокацией](/api/receiving/webhook/incoming-message/LocationMessage)
- [Входящее сообщение с контактом](/api/receiving/webhook/incoming-message/ContactMessage)


