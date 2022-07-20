# Входящее текстовое сообщение или сообщение с URL

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего текстового сообщения или сообщения с URL. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `extendedTextMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `extendedTextMessage`
`extendedTextMessageData` | **object** | Объект данных о принятом текстовом сообщении или URL ссылки
`quotedMessage` | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой

Поля объекта `extendedTextMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`text` | **string** | Текст ссылки или обычный текст
`description` | **string** | Описание ссылки, может быть пустым
`title` | **string** | Заголовок ссылки, может быть пустым
`jpegThumbnail` | **string** | Превью изображения в `base64` кодировке, может отсутствовать

Поля объекта `quotedMessage`

| Параметр      | Тип        | Описание                             |
| ------------- | ---------- | ------------------------------------ |
| `stanzaId`    | **string** | id цитируемого сообщения             |
| `participant` | **string** | id отправителя цитируемого сообщения |
| `typeMessage` | **string** | Тип цитируемого сообщения            |

Остальные поля заполняются в зависимости от типа цитируемого сообщения и идентичны полям входящих сообщений описаннных в разделе [Входящие сообщения](Webhook-IncomingMessageReceived.md)

### Пример тела уведомления {#webhook-example-body}

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
    "messageData": {
        "typeMessage": "extendedTextMessage",
        "extendedTextMessageData": {
            "text": "https://green-api.com/docs/video",
            "description": "Green API docs shows how you can develop the WhatsApp Bot",
            "title": "How to develop WhatsApp Bot",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFxQYG=="
        }
    }
}
```

### Пример тела уведомления входящего сообщения с ссылкой или текстом и цитатой контакта {#webhook-example-body}

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
  "messageData": {
    "typeMessage": "quotedMessage",
    "extendedTextMessageData": {
      "text": "https://yandex.ru/former&utm_source=home&utm_content=main_informer&utm_term=main_number",
      "stanzaId": "0EA554E587820E35309858AE265BE7EA",
      "participant": "79001230000@c.us"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79061230000@c.us",
      "typeMessage": "contactMessage",
      "contact": {
        "displayName": "Green-Api",
        "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Green-Api\nitem1.TEL;waid=79001230000\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
      }
    }
  }
}
```

### Пример тела уведомления входящего сообщения с ссылкой и цитатой изображения {#webhook-example-body}

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
  "messageData": {
    "typeMessage": "quotedMessage",
    "extendedTextMessageData": {
      "text": "https://yandex.ru/pogoda/?utm_medium=source=home&utm_content=main_informer&utm_term=main_number",
      "stanzaId": "B4AA239D112CB2576897B3910FEDE26E",
      "participant": "79001230000@c.us"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79061230000@c.us",
      "typeMessage": "imageMessage",
      "downloadUrl": "",
      "caption": ""
    }
  }
}
```
