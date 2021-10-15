# Execute requests

To execute a request to the Green API, you have to execute GET or POST request at  

```
https://api.green-api.com/waInstance{{idInstance}}/{{method}}/{{apiTokenInstance}}
```

The request address is generated from the account number `idInstance` and the access key` apiTokenInstance`, which must be obtained in advance in [Your profile](https://cabinet.green-api.com) in accordance with [Before you start](before-start.md#parameters) section.

The required API method, described in [API documents](api/index.md) is used as `method` parameter. 

Example of a request to send a message by [SendMessage](api/sending/SendMessage.md) method:
```
https://api.green-api.com/waInstance1234/SendMessage/bde035edae3fc00bc116bd112297908d8145e5ba8decc5d884
```

## Request titles
Most requests should contain standard titles:

- `Content-Type` - `application/json`

In some cases titles may differ, for example, for [SendFileByUpload](api/sending/SendFileByUpload.md) file sending method  

## Debug requests

To debug requests to the Green API it is recommended to use [Postman collection](postman-collection.md)
