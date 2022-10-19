# Как принять и обработать уведомление
### Установка
```
pip install whatsapp-api-client-python
```
### Import 
```
from whatsapp_api_client_python import API
```
### Примеры
Полный пример можно посмотреть по ссылке: [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)

#### Как инициализировать объект

```
restApi = API.RestApi('https://api.green-api.com', 
                        ID_INSTANCE, 
                        API_TOKEN_INSTANCE)
```
Обратите внимание, что ключи можно получать из переменных среды:
```
from os import environ

ID_INSTANCE = environ['ID_INSTANCE']
API_TOKEN_INSTANCE = environ['API_TOKEN_INSTANCE']
```

#### Как принять и обработать уведомление

```
resultReceive = restApi.receiving.receiveNotification()
```

### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста | [sendText.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendText.py)
Пример отправки картинки по URL | [sendPictureByLink.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByLink.py)
Пример отправки картинки загрузкой с диска | [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)
Пример создание группы и отправка сообщения в группу | [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)
Пример получения входящих уведомлений | [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)
