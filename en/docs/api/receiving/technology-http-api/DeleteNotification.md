# DeleteNotification

The method is aimed for deleting an incoming notification from the notification queue. To specify what notification to delete, use `receiptId` parameter.
After receiving and processing an incoming notification, you need to delete the notification from the queue. This requires you to run this method. After calling the method, the notification will be considered received and processed and will be permanently deleted from the queue. Therefore, the next call of [ReceiveNotification](ReceiveNotification.md) method will return the next notification from the queue in the order in which notifications come to the queue.

> Incoming notifications are stored in the queue for 24 hours.

> Notifications are sent from the queue in [FIFO](https://ru.wikipedia.org/wiki/FIFO) order

## Request {#request}

To delete an incoming notification from the queue, you have to execute a request at:
```
DELETE https://api.green-api.com/waInstance{{idInstance}}/DeleteNotification/{{apiTokenInstance}}/{{receiptId}}
```

> Note that you have to use a request of `DELETE` type

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`receiptId` | **integer** | Yes | Receipt Id for deleting an incoming notification received by [ReceiveNotification](ReceiveNotification.md) method 


## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | -----
`result ` | **boolean** | Incoming notification deleting result: `true` - incoming notification successfully deleted from the queue; `false` - notification is not deleted - possible, if the notification was deleted earlier or `receiptId` doesn't correspond to the value previously received by [ReceiveNotification](ReceiveNotification.md) method


### Response body example {#response-example-body}

```json
{
    "result": true
}
```

### DeleteNotification errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../../common-errors.md) section

HTTP code | Error Id | Description
----- | ----- | -----
400 | `Parameter receiptId must be a Number` | `receiptId` parameter is not specified or contains non-digit characters 
400 | `Parameter idInstance not an integer` | `idInstance` parameter is not specified or contains non-digit characters 
400 | `Parameter apiTokenInstance not define` | `apiTokenInstance` parameter is not specified


## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/DeleteNotification/{{apiTokenInstance}}/1234567"

payload = {}
headers= {}

response = requests.request("DELETE", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

You can see the example of notifications receipt code on [NodeJS](https://nodejs.org) in the file [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js)
