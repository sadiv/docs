# How to send a text message
### Installation
```
pip install whatsapp-api-client-python
```
### Import 
```
from whatsapp_api_client_python import API
```
### Examples
You may see the full example at: [sendText.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendText.py)

#### How to initialize an object

```
restApi = API.RestApi('https://api.green-api.com', 
                        ID_INSTANCE, 
                        API_TOKEN_INSTANCE)
```
Please note that keys can be obtained from environment variables:
```
from os import environ

ID_INSTANCE = environ['ID_INSTANCE']
API_TOKEN_INSTANCE = environ['API_TOKEN_INSTANCE']
```
#### How to send a text message to a WhatsApp number

```
result = restApi.sending.sendMessage('79001234567@g.us', 'Message text')
```
### The full list of examples

Description |  Module
----- | ----- 
Example of sending text | [sendText.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendText.py)
Example of sending a picture by URL | [sendPictureByLink.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByLink.py)
Example of sending a picture by uploading from the disk | [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)
Example of a group creation and sending a message to the group | [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)
Example of incoming webhooks receiving | [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)
