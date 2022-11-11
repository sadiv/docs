# Как отправить текстовое сообщение
### Установка
```
pip install whatsapp-api-client-python
```
### Import 
```
from whatsapp_api_client_python import API
```
### Примеры
Пример отправки текста | [sendTextMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendTextMessage.py)

#### Как инициализировать объект

```
greenAPI = API.GreenApi(ID_INSTANCE, API_TOKEN_INSTANCE)
```
Обратите внимание, что ключи можно получать из переменных среды:
```
from os import environ

ID_INSTANCE = environ['ID_INSTANCE']
API_TOKEN_INSTANCE = environ['API_TOKEN_INSTANCE']
```
#### Как отправить текстовое сообщения на номер WhatsApp

```
result = greenAPI.sending.sendMessage('79001234567@c.us', 'Message text')
```
### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста | [sendTextMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendTextMessage.py)
Пример отправки картинки по URL | [sendPictureByLink.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByLink.py)
Пример отправки картинки загрузкой с диска | [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)
Пример создание группы и отправка сообщения в группу | [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)
Пример получения входящих уведомлений | [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)
