# DeleteNotification

Метод предназначен для удаления входящего уведомления из очереди уведомлений.
После получения и обработки входящего уведомления требуется удалить уведомление из очереди. Для этого требуется выполнить данный метод. После вызова метода уведомление будет считаться принятым и обработанным и будет безвозвратно удалено из очереди. Таким образом следующий вызов метода [ReceiveNotification](ReceiveNotification.md) вернет следующее уведомление из очереди в порядке поступления уведомлений в очередь.

> Срок хранения входящих уведомлений в очереди составляет 24 часа.

> Уведомления отдаются из очереди в порядке [FIFO](https://ru.wikipedia.org/wiki/FIFO)

## Запрос {#request}

Для удаления входящего уведомления из очереди требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/DeleteNotification/{{apiTokenInstance}}/{{receiptId}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`receiptId` | **integer** | Да | Идентификатор доставки для удаления входящего уведомления, полученный методом [ReceiveNotification](ReceiveNotification.md)


## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | -----
`result ` | **boolean** | Результат удаления входящего уведомления: `true` - входящее уведомление успешно удалено из очереди; `false` - уведомление не удалено - возможно, когда уведомление было удалено ранее, или `receiptId` не соответствует ранее полученному значению методом [ReceiveNotification](ReceiveNotification.md)


### Пример тела ответа {#response-example-body}

```json
{
    "result": true
}
```

### Ошибки DeleteNotification {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../../common-errors.md)

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `Parameter receiptId must be a Number` | В качестве параметра `receiptId` требуется указывать число


## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/DeleteNotification/{{apiTokenInstance}}/1234567"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

Пример кода получения уведомлений на [NodeJS](https://nodejs.org) можно посмотреть в файле [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js)