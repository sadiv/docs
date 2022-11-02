# How to handle incoming notifications
### Installation
```
pip install whatsapp-api-client-python
```
### Import 
```
from whatsapp_api_client_python import API
```
### Examples
You may see the full example at: [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)

#### How to initialize an object

```
restApi = API.RestApi(ID_INSTANCE, API_TOKEN_INSTANCE)
```
Please note that keys can be obtained from environment variables:
```
from os import environ

ID_INSTANCE = environ['ID_INSTANCE']
API_TOKEN_INSTANCE = environ['API_TOKEN_INSTANCE']
```

#### Receiving incoming messages by HTTP API

The general concept of receiving data in the Green API is described [here](https://green-api.com/docs/api/receiving/)
To start receiving messages by the HTTP API, you need to execute the library method:

```
greenApi.webhooks.startReceivingNotifications(onEvent)
```

onEvent - your method which should contain parameters:
Parameter | Description
----- | -----
typewebhook | received message type (string)
body | message body (json)

Message body types and formats [here](https://green-api.com/docs/api/receiving/notifications-format/)

This method will be called when an incoming message is received. Next, process messages according to the business logic of your system.

### The full list of examples

Description |  Module
----- | ----- 
Example of sending text | [sendTextMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendTextMessage.py)
Example of sending a picture by URL | [sendPictureByLink.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByLink.py)
Example of sending a picture by uploading from the disk | [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)
Example of a group creation and sending a message to the group | [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)
Example of incoming webhooks receiving | [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)
