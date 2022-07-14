# Нажатие пользователя на значение списка выбора

В данном разделе описывается формат входящего уведомления объекта `messageData` для списка выбора. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `listResponseMessage`
`listResponseMessage` | **object** | Объект данных о нажатии пользователя на значение списка
`quotedMessage` | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой

Поля объекта `listResponseMessage`

Параметр | Тип | Описание
----- | ----- | -----
`title` | **string** | текст выбранного значения
`listType` | **string** | тип списка. 1 - выбор одного значения
`singleSelectReply` | **string** | id выбранного значения

### Пример тела уведомления {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1101000001,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1657025112,
    "idMessage": "A36C68A09C54796295FCAD20C15C534C",
    "senderData": {
        "chatId": "79001234567@c.us",
        "sender": "79001234567@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "listResponseMessage",
        "listResponseMessage": {
            "title": "Вариант 2",
            "listType": 1,
            "singleSelectReply": "option2"
        }
    }
}
```
