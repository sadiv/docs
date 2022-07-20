# Входящее сообщение с контактом

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения с контактом. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `contactMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр             | Тип        | Описание                                                                                        |
| -------------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`        | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `contactMessage`    |
| `contactMessageData` | **object** | Объект данных о принятом контакте.                                                              |
| `quotedMessage`      | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой |

Поля объекта `contactMessageData`

| Параметр      | Тип        | Описание                                     |
| ------------- | ---------- | -------------------------------------------- |
| `displayName` | **string** | Отображаемое имя контакта                    |
| `vcard`       | **string** | Структура VCard (визитной карточки контакта) |

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
    "typeMessage": "contactMessage",
    "contactMessageData": {
      "displayName": "Антиспам",
      "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:;Антиспам;;;\nFN:Антиспам\nitem1.TEL:*9035936232#\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79001235696@c.us",
      "typeMessage": "textMessage",
      "textMessage": "Привет"
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
    "typeMessage": "contactMessage",
    "contactMessageData": {
          "displayName": "Антиспам",
          "vcard": "BEGIN:VCARD\nVERSION:3.0\nFN:2 Лена\nitem1.TEL;waid=79001230000\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
    },
    },
    "quotedMessage": {
         "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
         "participant": "79061230000@c.us",
         "typeMessage": "imageMessage",
         "downloadUrl": "",
          "caption": ""
    }
  }
```

### Пример тела уведомления входящего сообщения с контактом и цитатой контакта {#webhook-example-body}

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
### Пример тела уведомления входящего сообщения с контактом и цитатой геопозиции {#webhook-example-body}

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
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
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
