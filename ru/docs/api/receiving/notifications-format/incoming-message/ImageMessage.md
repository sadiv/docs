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
| `caption`     | **string** | Описание под картинкой или видео |
| `fileName` | **string** | Название файла |
| `titleFile` | **string** | Заголовок файла |

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
    "typeMessage": "imageMessage",
    "fileMessageData": {
      "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/19136A974392FA8CF584D70DD0E1AEDF",
      "caption": "Картинка"
    }
  }
}
```

### Пример тела уведомления входящего сообщения с аудио и цитатой текстового сообщения {#webhook-example-body}

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
      "downloadUrl": "https://sw-media.storage.yandexcloud.net/9901742665/39c20293-eb8d-abdd-5fdd1b83820a.mpga",
      "fileName": "39c20293-eb8d-abdd-5fdd1b83820a.mpga",
      "titleFile": ""
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79001234569@c.us",
      "typeMessage": "textMessage",
      "textMessage": "Привет"
    }
  }
}
```

### Пример тела уведомления входящего сообщения с аудио и цитатой аудио/видео/документ {#webhook-example-body}

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
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79001234568@c.us",
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
    "typeMessage": "imageMessage",
    "fileMessageData": {
      "downloadUrl": "https://sw-media.storage.yandexcloud.net/0b-9784-483b-8426-e8d871d6de9f.jpeg",
      "caption": "",
      "fileName": "d417740b483b-8426-e8d871d6de9f.jpeg",
      "titleFile": ""
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
    "typeMessage": "imageMessage",
    "fileMessageData": {
      "downloadUrl": "https://sw-media.storage.yandexcloud.net/542ad819-166b-40a4-b0e1-279069cd03bb.jpeg",
      "caption": "",
      "fileName": "542ad819-166b-b0e1-279069cd03bb.jpeg",
      "titleFile": ""
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
