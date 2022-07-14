# Входящее сообщение с изображением, видео, аудио, документом

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения с изображением, видео, аудио или документом. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `imageMessage` || `videoMessage` || `documentMessage` || `audioMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение: `imageMessage`, `videoMessage`, `documentMessage`, `audioMessage`
`fileMessageData ` | **object** | Объект данных о принятом файле
`quotedMessage` | **object** | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой

Поля объекта `fileMessageData` 

Параметр | Тип | Описание
----- | ----- | -----
`downloadUrl` | **string** | Ссылка для скачивания файла
`caption` | **string** | Описание под файлом

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
        "typeMessage":"imageMessage",
        "fileMessageData":{
            "downloadUrl":"https://api.green-api.com/waInstance1234/downloadFile/19136A974392FA8CF584D70DD0E1AEDF",
            "caption":"Картинка"
        }
    }
}
```
