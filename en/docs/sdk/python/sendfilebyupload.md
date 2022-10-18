# Как отправить файл загрузкой с диска
### Установка
```
pip install whatsapp-api-client-python
```
### Import 
```
from whatsapp_api_client_python import API
```
### Примеры
Полный пример можно посмотреть по ссылке: [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)

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

#### Как отправить файл загрузкой с диска

```
result = restApi.sending.sendFileByUpload('120363025955348359@g.us', 
        'C:\Games\PicFromDisk.png', 
        'PicFromDisk.png', 'Picture from disk')
```
### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста | [sendText.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendText.py)
Пример отправки картинки по URL | [sendPictureByLink.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByLink.py)
Пример отправки картинки загрузкой с диска | [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)
Пример создание группы и отправка сообщения в группу | [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)
Пример получения входящих уведомлений | [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)
