# GetContacts

The method is aimed for getting a list of the current account contacts.

Sends contacts of all recipients whom the account connected with.
Parameter "contact name" 'name' takes on a value based on the below criteria:
1) If the account is recorded in the phonebook, then we get the name from the book;
2) If the account is not recorded in the phonebook, then we get the name from WhatsApp account;
3) If the account is not recorded in the phone book and WhatsApp account name is not assigned, then we get an empty field. 

## Request {#request}

To get contacts, you have to execute a request at:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetContacts/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`id` | **string** | [User or group chat Id](../chat-id.md)
`name` | **string** | Contact name
`type` | **string** | Contact type. Possible variants:
||`user` - contact belongs to a user
||`group` - contact is a group chat 


### Response body example {#response-example-body}

```json
[
    {
        "id": "79001234567@c.us",
        "name": "Ivan Petrov",
        "type": "user"
    },
    {
        "id": "79001234568@c.us",
        "name": "Lyusya Sidorova",
        "type": "user"
    },
    {
        "id": "79001234569-1479621234@g.us",
        "name": "My group",
        "type": "group"
    }
]
```

### GetContacts errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## Python request example  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getContacts/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
