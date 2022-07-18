# Входящее сообщение с изображением, видео, аудио, документом

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения с изображением, видео, аудио или документом. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `imageMessage` || `videoMessage` || `documentMessage` || `audioMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр          | Тип        | Описание                                                                                                                                       |
| ----------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение: `imageMessage`, `videoMessage`, `documentMessage`, `audioMessage` |
| `fileMessageData` | **object** | Объект данных о принятом файле                                                                                                                 |
| `quotedMessage`   | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой                                                |

Поля объекта `fileMessageData`

| Параметр      | Тип        | Описание                    |
| ------------- | ---------- | --------------------------- |
| `downloadUrl` | **string** | Ссылка для скачивания файла |
| `caption`     | **string** | Описание под файлом         |

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
    "typeMessage": "imageMessage",
    "fileMessageData": {
      "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/19136A974392FA8CF584D70DD0E1AEDF",
      "caption": "Картинка"
    }
  }
}
```

### Пример тела уведомления входящего сообщения с изображением и цитатой текстового сообщения {#webhook-example-body}

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
      "typeMessage": "imageMessage",
      "downloadUrl": "",
      "caption": ""
    }
  }
}
```

### Пример тела уведомления входящего сообщения с изображением и цитатой изображения {#webhook-example-body}

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
          "downloadUrl": "https://s/990173687/801078ab-3340-4еbe4aa5.jpeg",
         "caption": "",
         "fileName": "801078ab-3340-4f78-е9978be4aa5.jpeg",
          "titleFile": ""
    },
    "quotedMessage": {
         "participant": "79001234568@c.us",
         "typeMessage": "imageMessage",
         "downloadUrl": "",
         "caption": ""
    }
  }
}
```
### Пример тела уведомления входящего сообщения с изображением и цитатой аудио/видео/документ {#webhook-example-body}

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
    "typeMessage": "audioMessage",
    "fileMessageData": {
          "downloadUrl": "https://s/990173687/801078ab-3340-4e4aa5.jpeg",
         "caption": "",
         "fileName": "801078ab-3340-4f78-е9978be4aa5.jpeg",
         "titleFile": ""
    },
    "quotedMessage": {
          "participant": "79001234568@c.us",
          "typeMessage": "imageMessage",
          "downloadUrl": "",
         "caption": ""
    }
  }
}
```

### Пример тела уведомления входящего сообщения с изображением и цитатой ссылка {#webhook-example-body}

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
          "participant": "79061230000@c.us",
         "typeMessage": "imageMessage",
         "downloadUrl": "",
          "caption": ""
    }
  }
}
```
### Пример тела уведомления входящего сообщения с изображением и цитатой геопозиция {#webhook-example-body}

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
          "nameLocation": "",
          "address": "",
         "jpegThumbnail": "",
         "latitude": 74.5922641,
         "longitude": 59.6645355
    },
    "quotedMessage": {
          "participant": "79061230000@c.us",
         "typeMessage": "imageMessage",
         "downloadUrl": "",
          "caption": ""
    }
  }
}
```
### Пример тела уведомления входящего сообщения с изображением и цитатой контакт {#webhook-example-body}

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
          "participant": "79061230000@c.us",
         "typeMessage": "imageMessage",
         "downloadUrl": "",
          "caption": ""
    }
  }
}
```