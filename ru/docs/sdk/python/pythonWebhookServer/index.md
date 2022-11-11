# Python Webhook server library

[![Python application](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-app.yml/badge.svg?branch=master)](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-app.yml)
[![Upload Python Package](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-publish.yml/badge.svg)](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-publish.yml)

Python библиотека для интеграции с мессенджером WhatsAPP через API сервиса [green-api.com](https://green-api.com). Чтобы воспользоваться библиотекой нужно получить регистрационный токен и id аккаунта в [личном кабинете](https://console.green-api.com). Есть бесплатный тариф аккаунта разработчика.

#### API

Документация к REST API находится по [ссылке](https://green-api.com/docs/api/). Библиотека является оберткой к REST API, поэтому документация по ссылке выше применима и к самой библиотеке.

#### Подготовка среды

На машине должен быть установлен Python 3 последней версии, который можно скачать 
с официального сайта: [python.org](https://www.python.org/downloads/)

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

#### Перенаправление вебхуков на сервер

Для перенаправления вебхуков событий WhatsApp нужно в консоле [кабинета Green-Api](https://console.green-api.com/instanceList/) установить для инстанса адрес отправки уведомлений:

![`Адрес отправки уведомлений`](../../../assets/ChangeWebhookServerURL.png)

#### [Пример подготовки среды сервера на операционной системе Ubuntu](serverUbuntu.md)
#### [Пример подготовки среды сервера на операционной системе Windows](serverWindows.md)
#### [Пример разворачивания среды сервера в контейнере Docker](serverDocker.md)
