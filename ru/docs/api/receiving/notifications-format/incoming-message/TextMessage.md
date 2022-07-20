# Входящее текстовое сообщение

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего текстового сообщения. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `textMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр          | Тип        | Описание                                                                                        |
| ----------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `textMessage`       |
| `textMessageData` | **object** | Объект данных о текстовом сообщении                                                             |
| `quotedMessage`   | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой |

Поля объекта `textMessageData`

| Параметр      | Тип        | Описание            |
| ------------- | ---------- | ------------------- |
| `textMessage` | **string** | Текстовое сообщение |

Поля объекта `quotedMessage`

| Параметр      | Тип        | Описание            |
| ------------- | ---------- | ------------------- |
| `stanzaId` | **string** | id цитируемого сообщения |
| `participant` | **string** | id отправителя цитируемого сообщения |
| `typeMessage` | **string** | Тип цитируемого сообщения |

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
    "typeMessage": "textMessage",
    "textMessageData": {
      "textMessage": "I use Green-API to send this message to you!"
    }
  }
}
```

### Пример тела уведомления с цитатой текстового сообщения {#webhook-example-body}

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
      "text": "Это",
      "stanzaId": "B7F33B8947D872F30FAA646FEDCDE2EC",
      "participant": "79001234568@c.us"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79001234568@c.us",
      "typeMessage": "textMessage",
      "textMessage": "Привет"
    }
  }
}
```

### Пример тела уведомления текстового сообщения с цитатой сообщения изображения/видео/аудио/документ {#webhook-example-body}

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
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79061230000@c.us",
      "typeMessage": "imageMessage",
      "downloadUrl": "",
      "caption": ""
    }
  }
}
```

### Пример тела уведомления с цитатой сообщения контакт {#webhook-example-body}

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

### Пример тела уведомления с цитатой сообщения геопозиция {#webhook-example-body}

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
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
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

### Пример тела уведомления с цитатой сообщения ссылка {#webhook-example-body}

```json
{
  "typeWebhook": "incomingMessageReceived",
  "instanceData": {
    "idInstance": 1234,
    "wid": "7000000000@c.us",
    "typeInstance": "whatsapp"
  },
  "timestamp": 1658261933,
  "idMessage": "CDF9219DD08D3D84CD4E621122AFBFFD",
  "senderData": {
    "chatId": "79000000000@c.us",
    "sender": "79000000000@c.us",
    "senderName": "Green API"
  },
  "messageData": {
    "typeMessage": "quotedMessage",
    "extendedTextMessageData": {
      "text": "Hello",
      "stanzaId": "6FFC3BF49BEE0CF966397321C4E3D3DF",
      "participant": "79000000000@c.us"
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79000000000@c.us",
      "typeMessage": "extendedTextMessage",
      "textMessage": "https://api.green-api.com/send/?phone=7000000000&text&type=phone_number&app_absent=0",
      "extendedTextMessage": {
        "description": " is free and offers simple, secure, reliable messaging and calling, available on phones all over the world.",
        "title": "Share on ",
        "previewType": "None",
        "jpegThumbnail": null
      }
    }
  }
}
```
