# Входящее сообщение с геолокацией

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения с геолокацией. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `locationMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `locationMessage`
`locationMessageData` | **object** | Объект данных о принятой геолокации
`quotedMessage` | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой

Поля объекта `locationMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`latitude` | **double** | Широта локации
`longitude` | **double** | Долгота локации
`jpegThumbnail` | **string** | Превью изображения в `base64` кодировке

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
        "typeMessage": "locationMessage",
        "locationMessageData": {
            "latitude": 12.345678910111213,
            "longitude": 14.151617181920212,
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFx="
        }
    }
}

```

### Пример тела уведомления входящего сообщения с геопозицией и цитатой тестового сообщения {#webhook-example-body}

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
      "text": "Адрес",
      "stanzaId": "CA5654B8E8806ED7D033E758E7463AB9",
      "participant": "79001230000@c.us"
    },
    "quotedMessage": {
      "participant": "79060002233@c.us",
      "typeMessage": "locationMessage",
      "location": {
             "nameLocation": "",
             "address": "",
              "jpegThumbnail": "",
               "latitude": 72.5922702,
                "longitude": 39.6645388
      }
    }
  }
}

```

### Пример тела уведомления входящего сообщения с геопозицией и цитатой изображения/аудио/видео/документа {#webhook-example-body}

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
    "typeMessage": "imageMessage",
    "fileMessageData": {
      "downloadUrl": "https://sw-media.storage.yandexcloud.net/0b-9784-483b-8426-e8d871d6de9f.jpeg",
      "caption": "",
      "fileName": "d417740b483b-8426-e8d871d6de9f.jpeg",
      "titleFile": ""
    },
    "quotedMessage": {
      "participant": "79060002233@c.us",
      "typeMessage": "locationMessage",
      "location": {
             "nameLocation": "",
             "address": "",
              "jpegThumbnail": "",
               "latitude": 72.5922702,
                "longitude": 45.6645388
         }
    }
  }
}

```

### Пример тела уведомления входящего сообщения с геопозицией и цитатой контакт {#webhook-example-body}

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
    "typeMessage": "contactMessage",
    "contactMessageData": {
      "displayName": "Фонд",
      "vcard": "BEGIN:VCARD\nVERSION:3.0\nFN:2 Сердца\nitem1.TEL;waid=79200000102\nitem1.X-ABLabel:Новый тип\nEND:VCARD"
    },
    "quotedMessage": {
      "participant": "79060002233@c.us",
      "typeMessage": "locationMessage",
      "location": {
             "nameLocation": "",
             "address": "",
              "jpegThumbnail": "",
               "latitude": 72.5922702,
                "longitude": 45.6645388
        }
    }
  }
}

```

### Пример тела уведомления входящего сообщения с геопозицией и цитатой ссылка {#webhook-example-body}

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
      "text": "https://yandex.ru/campaign=informer&utm_source=home&utm_content=main_informer&utm_term=main_number",
      "stanzaId": "CA5654B8E8806ED7D033E758E7463AB9",
      "participant": "790100022110@c.us"
    },
    "quotedMessage": {
      "participant": "79060002233@c.us",
      "typeMessage": "locationMessage",
      "location": {
             "nameLocation": "",
             "address": "",
              "jpegThumbnail": "",
               "latitude": 72.5922702,
                     "longitude": 45.6645388
      }
    }
  }
}

```

### Пример тела уведомления входящего сообщения с геопозицией и цитатой геопозиция {#webhook-example-body}

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
      "text": "https://yandex.ru/campaign=informer&utm_source=home&utm_content=main_informer&utm_term=main_number",
      "stanzaId": "CA5654B8E8806ED7D033E758E7463AB9",
      "participant": "790100022110@c.us"
    },
    "quotedMessage": {
      "participant": "79060002233@c.us",
      "typeMessage": "locationMessage",
      "location": {
             "nameLocation": "",
             "address": "",
              "jpegThumbnail": "",
               "latitude": 72.5922702,
                "longitude": 45.6645388
        }
    }
  }
}
