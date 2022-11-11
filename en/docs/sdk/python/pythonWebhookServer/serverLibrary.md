# Библиотека Python Webhook server

#### Подготовка среды

На машине должен быть установлен Python 3 последней версии, который можно скачать 
с официального сайта: [python.org](https://www.python.org/downloads/)

#### Установка библиотеки

```
pip3 install whatsapp-api-webhook-server-python
```

#### Запуск сервера

Для использования в ваших решениях достаточно импортировать класс webhooksHandler
```
import whatsapp_api_webhook_server_python.webhooksHandler as webhooksHandler
```

Старт сервера:
```
webhooksHandler.startServer('127.0.0.1', 80, onEvent)
```

onEvent - метод обработки вебхуков, который определяет разработчик.
В методе должно быть три параметра:
- webhooksHandler - экземляр класса библиотеки
- typeWebhook - тип вебхука
- body - тело сообщения

См. пример [echo.py](https://github.com/green-api/whatsapp-api-webhook-server-python/blob/master/examples/echo.py)