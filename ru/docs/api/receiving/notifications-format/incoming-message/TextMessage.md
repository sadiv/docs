# Входящее текстовое сообщение

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего текстового сообщения. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `textMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `textMessage`
`textMessageData` | **object** | Объект данных о текстовом сообщении
`quotedMessage` | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой

Поля объекта `textMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`textMessage` | **string** | Текстовое сообщение

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
    "messageData":{
        "typeMessage":"textMessage",
        "textMessageData":{
            "textMessage":"I use Green-API to send this message to you!"
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
            "participant": "79001234568@c.us",
            "typeMessage": "textMessage",
            "textMessage": "Привет"
        }
    }
}

```
### Пример тела уведомления с цитатой сообщения видео/аудио/документ {#webhook-example-body}

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
            "participant": "79001234569@c.us",
           "typeMessage": "textMessage",
           "textMessage": "Привет"
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
    "typeMessage": "contactMessage",
    "contactMessageData": {
         "displayName": "Антиспам",
         "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:;Антиспам;;;\nFN:Антиспам\nitem1.TEL:*9035936232#\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
    },
    "quotedMessage": {
           "participant": "79001235696@c.us",
           "typeMessage": "textMessage",
           "textMessage": "Привет"
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
    "typeMessage": "locationMessage",
    "locationMessageData": {
          "nameLocation": "",
          "address": "",
         "jpegThumbnail": "217",
         "latitude": 74.5922641,
         "longitude": 59.6645355
    },
    "quotedMessage": {
           "participant": "79001230022@c.us",
           "typeMessage": "textMessage",
           "textMessage": "Привет"
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
         "stanzaId": "07CFFEB422750ADBFBD0E355AF385B37",
         "participant": "79001230000@c.us"
    },
    "quotedMessage": {
           "participant": "79001235696@c.us",
           "typeMessage": "textMessage",
           "textMessage": "Привет"
    }
  }
}
```