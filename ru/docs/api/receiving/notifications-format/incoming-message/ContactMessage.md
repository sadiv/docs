# Входящее сообщение с контактом

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения с контактом. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `contactMessage`


## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `contactMessage`
`contactMessageData` | **object** | Объект данных о принятом контакте.
`quotedMessage` | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой

Поля объекта `contactMessageData` 

Параметр | Тип | Описание
----- | ----- | -----
`displayName` | **string** | Отображаемое имя контакта
`vcard` | **string** | Структура VCard (визитной карточки контакта)

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
        "typeMessage": "contactMessage",
        "contactMessageData": {
            "displayName": "Виктор Андреевич",
            "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Андреевич;Виктор;;;\nFN:Виктор Андреевич\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
        }
    }
}

```
### Пример тела уведомления входящего сообщения с контактом и цитатой текстового сообщения {#webhook-example-body}

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
      "text": "Ответ",
      "stanzaId": "B4AA239D112CB2576897B3910FEDE26E",
      "participant": "79001230000@c.us"
    },
    "quotedMessage": {
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

### Пример тела уведомления входящего сообщения с контактом и цитатой изображения {#webhook-example-body}

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
         "downloadUrl": "https://sw-media.storage.yandexcloud.net/542ad819-166b-40a4-b0e1-279069cd03bb.jpeg",
         "caption": "",
         "fileName": "542ad819-166b-b0e1-279069cd03bb.jpeg",
            "titleFile": ""
    },
    "quotedMessage": {
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

### Пример тела уведомления входящего сообщения с контактом и цитатой аудио/видео/документ {#webhook-example-body}

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
    "typeMessage": "videoMessage",
    "fileMessageData": {
        "downloadUrl": "https://sw-media.storage.yandexcloud.net/99017665/5cc6-4280-94b4-6c96d4d79a4c.mp4",
        "caption": "",
         "fileName": "5cc6-4280-94b4-6c96d4d79a4c.mp4",
        "titleFile": ""
    },
    "quotedMessage": {
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

### Пример тела уведомления входящего сообщения с контактом и цитатой ссылка {#webhook-example-body}

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

### Пример тела уведомления входящего сообщения с контактом и цитатой контакт {#webhook-example-body}

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
           "displayName": "",
        "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Фонд;\nitem1.TEL;waid=79001203030:/em1.X-ABLabel:Новый тип\nEND:VCARD"
    },
    "quotedMessage": {
         "participant": "79061230000@c.us",
         "typeMessage": "contactMessage",
         "contact": {
         "displayName": "Green-Api",
         "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Green-Api\nitem1.TEL;waid=79001230000\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
        }
    }
  }
}