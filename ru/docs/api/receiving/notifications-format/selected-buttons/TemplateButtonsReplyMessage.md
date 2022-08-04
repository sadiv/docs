# Выбор шаблонной кнопки

В данном разделе описывается формат входящего уведомления объекта `messageData` для шаблонных кнопок. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](/../docs/api/receiving/notifications-format/). 

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `templateButtonsReplyMessage`
`templateButtonReplyMessage` | **object** | Объект данных о нажатии пользователя на кнопку

Поля объекта `templateButtonReplyMessage`

Параметр | Тип | Описание
----- | ----- | -----
`selectedIndex` | **string** | числовой индекс нажатой кнопки
`selectedId` | **string** | идентификатор нажатой кнопки
`selectedDisplayText` | **string** | текст нажатой кнопки
`stanzaId` | **string** | ID сообщения с кнопками

### Пример тела уведомления {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1101000001,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1656315272,
    "idMessage": "9BB19BB0D568BA7B185EEAD21A33D317",
    "senderData": {
        "chatId": "79001234567@c.us",
        "sender": "79001234567@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "templateButtonReplyMessage",
        "templateButtonReplyMessage": {
            "stanzaId": "BAE53AFDD5F0C137",
            "selectedIndex": 2,
            "selectedId": "id1",
            "selectedDisplayText": "red"
        },
    }
}
```
