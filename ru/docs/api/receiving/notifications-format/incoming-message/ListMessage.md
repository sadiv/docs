# Входящее сообщение со списком выбора

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения со списком выбора. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `listMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр| Тип | Описание  |
| ----------------- | ---------- | ------------ |
| `typeMessage`     | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `listMessage`       |
| `listMessage` | **object** | Объект данных со списком |
| `quotedMessage`   | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой |

Поля объекта `listMessage`

| Параметр      | Тип        | Описание            |
| ------------- | ---------- | ------------------- |
| `contentText` | **string** | Текстовое сообщение тела кнопок|
|`title` | **string** | Нет | Заголовок сообщения|
| `footer` | **string** | Текстовое сообщение подвала кнопок|
| `listMessage` | **object** | Объект данных с кнопками |
|`buttonText` | **string** | Нет | надпись на кнопке списка выбора|
|`sections` | **array** | Да | значения списка выбора|

Поля массива `sections`

| Параметр | Тип        | Описание                |
| -------- | ---------- | ----------------------- |
| `title`  | **string** | заголовок списка выбора |
| `rows`   | **array**  | значения списка выбора  |

Поля массива `rows`

| Параметр | Тип        | Описание                      |
| -------- | ---------- | ----------------------------- |
| `title`  | **string** | текст значения списка         |
| `rowId`  | **string** | идентификатор значения списка |
| `description` | **string** | описание значения списка |

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
        "typeMessage": "listMessage",
        "listMessage": {
            "contentText": "Hello",
            "title": "заголовок",
            "footer": "Hello",
            "buttonText": "Список действий",
            "sections": [
                {
                    "title": "Секция 1",
                    "rows": [
                        {
                            "title": "Вариант 1",
                            "rowId": "option1"
                        },
                        {
                            "title": "Вариант 2",
                            "rowId": "option2",
                            "description": "Пояснение"
                        }
                    ]
                },
                {
                    "title": "Секция 2",
                    "rows": [
                        {
                            "title": "Опция 3",
                            "rowId": "option3"
                        },
                        {
                            "title": "Опция 4",
                            "rowId": "option4",
                            "description": "Пояснение"
                }
            ]
        }
    }
}
```
