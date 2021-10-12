# ReceiveNotification

The method is aimed for receiving one incoming notification from the notifications queue.

> ReceiveNotification method waits for a notification receipt for 20 sec. The method call ends with an empty response if a timeout is reached. If a notification comes to the queue within 20 seconds, the method call is completed, and the method returns the received notification. 

After receiving and processing an incoming notification, you need to delete the notification from the queue. This requires you to run [DeleteNotification](DeleteNotification.md) method. After calling [DeleteNotification](DeleteNotification.md) method, the notification will be considered received and processed and will be permanently deleted from the queue. Therefore, the next call of [ReceiveNotification](#request) method will return the next notification from the queue in the order in which notifications come to the queue.

> Incoming notifications are stored in the queue for 24 hours.

> Notifications are sent from the queue in [FIFO](https://ru.wikipedia.org/wiki/FIFO) order

## Request {#request}

To get the next incoming notification from the queue, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/ReceiveNotification/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../../before-start.md#parameters) section.


## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | -----
`receiptId ` | **integer** | Receipt Id for deleting an incoming notification by [DeleteNotification](DeleteNotification.md) method
`body ` | **object** | Incoming notification in accordance with [Incoming notifications format](../notifications-format/index.md)  

### Response body example {#response-example-body}

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

### ReceiveNotification errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../../common-errors.md) section

HTTP code | Error Id | Description
----- | ----- | -----
400 | `Parameter idInstance not an integer` | `idInstance` parameter is not specified or contains non-digit characters
400 | `Parameter apiTokenInstance not define` | `apiTokenInstance` is not specified

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/ReceiveNotification/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

You can see the example of notifications receipt code on [NodeJS](https://nodejs.org) in the file [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js)
