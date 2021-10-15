# SendContact

The method is aimed for sending a contact message. 
Contact visit card is created and sent to a chat.
The message will be added to the send queue.
The rate at which messages are sent from the queue is managed by [Message sending delay](../send-messages-delay.md) parameter.

## Request {#request}

To send a contact message, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/sendContact/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`contact` | **object** | Yes | Contact object
`quotedMessageId` | **string** | No | Quoted message Id, if present the message will be sent quoting the specified chat message

`contact` object parameters:

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`phoneContact ` | **integer** | Yes | contact phone number in international format (no +) 11 or 12 digits
`firstName` | **string** | If `middleName`, `lastName`, `company` not specified | Contact name
`middleName` | **string** | If `firstName`, `lastName`, `company` not specified | Contact middle name
`lastName` | **string** | If `middleName`, `firstName`, `company` not specified | Contact last name
`company` | **string** | If `middleName`, `lastName`, `firstName` not specified | Contact company name

### Пример тела запроса {#request-example-body}

Sending a message to a personal chat:
```json
{
    "chatId": "79001234567@c.us",
    "contact": {
        "phoneContact": 79001234568,
        "firstName": "Artem",
        "middleName": "Petrovich",
        "lastName": "Evpatoriysky",
        "company": "Bicycle"
    }
}
```

Sending a message to a group chat:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "contact": {
        "phoneContact": 79001234568,
        "firstName": "Artem",
        "middleName": "Petrovich",
        "lastName": "Evpatoriysky",
        "company": "Bicycle"
    }
}
```

Sending a quoted message:
```json
{
    "chatId": "79001234567@c.us",
    "quotedMessageId": "361B0E63F2FDF95903B6A9C9A102F34B",
    "contact": {
        "phoneContact": 79001234568,
        "firstName": "Artem",
        "middleName": "Petrovich",
        "lastName": "Evpatoriysky",
        "company": "Bicycle"
    }
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | -----
`idMessage ` | **string** | Outgoing message Id 

### Response body example {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### SendContact errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendContact/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"contact\": {\r\n\t\t\"phoneContact\": 79001234568,\r\n    \t\"firstName\": \"Артем\",\r\n\t\t\"middleName\": \"Петрович\",\r\n\t\t\"lastName\": \"Евпаторийский\",\r\n\t\t\"company\": \"Велосипед\"\r\n\t}\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
