# ReceiveNotification

Метод предназначен для получения одного входящего уведомления из очереди уведомлений.

> Метод ReceiveNotification ожидает получения уведомления в течение 20 сек. Вызов метода завершается с пустым ответом в случае достижения таймаута. Если в течение 20 сек в очереди появляется уведомление, то вызов метода завешается, и метод возвращает полученное уведомление. 

После получения и обработки входящего уведомления требуется удалить уведомление из очереди. Для этого требуется выполнить метод [DeleteNotification](DeleteNotification.md). После вызова метода [DeleteNotification](DeleteNotification.md) уведомление будет считаться принятым и обработанным и будет безвозвратно удалено из очереди. Таким образом следующий вызов метода [ReceiveNotification](#request) вернет следующее уведомление из очереди в порядке поступления уведомлений в очередь.

> Срок хранения входящих уведомлений в очереди составляет 24 часа.

> Уведомления отдаются из очереди в порядке [FIFO](https://ru.wikipedia.org/wiki/FIFO)

## Запрос {#request}

Для получения следующего входящего уведомления из очереди требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/ReceiveNotification/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../../before-start.md#parameters).


## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | -----
`receiptId ` | **integer** | Идентификатор доставки для удаления входящего уведомления методом [DeleteNotification](DeleteNotification.md)
`body ` | **object** | Входящее уведомление согласно [Формату входящих уведомлений](../notifications-format/index.md)  

### Пример тела ответа {#response-example-body}

```json
{
    "receiptId": 1234567,
    "body": {
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
}
```

### Ошибки ReceiveNotification {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/ReceiveNotification/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

Пример кода получения уведомлений на [NodeJS](https://nodejs.org) можно посмотреть в файле [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js)