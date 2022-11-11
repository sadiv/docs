# Как обрабатывать входящие уведомления
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
greenAPI = API.GreenApi(ID_INSTANCE, API_TOKEN_INSTANCE)
```
Обратите внимание, что ключи можно получать из переменных среды:
```
from os import environ

ID_INSTANCE = environ['ID_INSTANCE']
API_TOKEN_INSTANCE = environ['API_TOKEN_INSTANCE']
```

#### Получение входящих сообщений через HTTP API

Общая концепция получения данных в Green API описана [здесь](https://green-api.com/docs/api/receiving/)
Для старта получения сообщений через HTTP API требуется выполнить метод библиотеки:

```
greenApi.webhooks.startReceivingNotifications(onEvent)
```

onEvent - ваш метод, который должен содержать параметры:

Параметр |  Описание
----- | -----
typeWebhook | тип полученного сообщения (строка)
body | тело сообщения (json)

Типы и форматы тел сообщений [здесь](https://green-api.com/docs/api/receiving/notifications-format/)

Этот метод будет вызываться при получении входящего сообщения. Далее обрабатываете сообщения согласно бизнес-логике вашей системы.

### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста | [sendTextMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendTextMessage.py)
Пример отправки картинки по URL | [sendPictureByLink.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByLink.py)
Пример отправки картинки загрузкой с диска | [sendPictureByUpload.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/sendPictureByUpload.py)
Пример создание группы и отправка сообщения в группу | [createGroupAndSendMessage.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/createGroupAndSendMessage.py)
Пример получения входящих уведомлений | [receiveNotification.py](https://github.com/green-api/whatsapp-api-client-python/blob/master/examples/receiveNotification.py)
