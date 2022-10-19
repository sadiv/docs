# Как создать группу и отправить в неё сообщение
### Установка
```
pip install whatsapp-api-client-python
```
### Import 
```
from whatsapp_api_client_python import greenAPI
```
### Примеры
Полный пример можно посмотреть по ссылке: [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)

#### Как инициализировать объект

```
restApi = API.RestApi(ID_INSTANCE, API_TOKEN_INSTANCE)
```
Обратите внимание, что ключи можно получать из переменных среды:
```
from os import environ

ID_INSTANCE = environ['ID_INSTANCE']
API_TOKEN_INSTANCE = environ['API_TOKEN_INSTANCE']
```

#### Как создать группу и отправить в неё сообщение

```
chatIds = [
    "79001234567@c.us"
]
resultCreate = restApi.groups.createGroup('GroupName', 
    chatIds)

if resultCreate.code == 200:
    resultSend = restApi.sending.sendMessage(resultCreate.data['chatId'], 
        'Message text')
```

ВАЖНО: Если попытаться создать группу с несуществующим номером WhatsApp 
может заблокировать номер отправителя. Номер в примере не существует.

### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста | [sendTextMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendTextMessage.py)
Пример отправки картинки по URL | [sendPictureByLink.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByLink.py)
Пример отправки картинки загрузкой с диска | [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)
Пример создание группы и отправка сообщения в группу | [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)
Пример получения входящих уведомлений | [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)
