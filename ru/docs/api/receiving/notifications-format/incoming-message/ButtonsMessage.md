# Входящее сообщение с кнопками

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения с кнопками. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `buttonsMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр          | Тип        | Описание                                                                                        |
| ----------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `buttonsMessage`       |
| `buttonsMessage` | **object** | Объект данных с кнопками                                                           |
| `quotedMessage`   | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой |

Поля объекта `buttonsMessage`

| Параметр      | Тип        | Описание            |
| ------------- | ---------- | ------------------- |
| `contentText` | **string** | Текстовое сообщение тела кнопок|
| `footer` | **string** | Текстовое сообщение подвала кнопок|
| `buttons`   | **object** | Объект данных с кнопками |

Поля объекта `buttons`

| Параметр      | Тип        | Описание            |
| ------------- | ---------- | ------------------- |
| `buttonId` | **string** | id кнопки |
| `buttonText` | **string** | Текст кнопки |

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
        "typeMessage": "buttonsMessage",
        "buttonsMessage": {
            "contentText": "Hello",
            "footer": "Hello",
            "buttons": [
                {
                    "buttonId": "1",
                    "buttonText": "green"
                },
                {
                    "buttonId": "2",
                    "buttonText": "red"
                },
                {
                    "buttonId": "3",
                    "buttonText": "blue"
                }
            ]
        }
    }
}
```
