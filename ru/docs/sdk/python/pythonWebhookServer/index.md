# Python Webhook server library

[![Python application](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-app.yml/badge.svg?branch=master)](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-app.yml)
[![Upload Python Package](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-publish.yml/badge.svg)](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-publish.yml)

#### Настройка

Перед началом работы убедитесь, что вы выполнили настройку инстанса для получения вебхуков на ваш сервер [Настройка личного кабинета](../../../api/receiving/technology-webhook-endpoint.md#cabinet).

- Перейдите в [консоль GreenAPI](https://console.green-api.com/)

- Создайте бесплатный инстанс на тарифе Developer

- В настройках инстанса укажите адрес вашего сервера вебхуков. Допускается указывать как доменное имя, так и IP-адрес

- Включите вебхуки, которые треубется получать. См. картинку в [настройках личного кабинета](../../../api/receiving/technology-webhook-endpoint.md#cabinet)

- Сохраните настройки инстанса

- Авторизуйте инстанс, считав QR-код с телефона

- Напишите любое сообщение в WhatsApp на номер, который подключен к инстансу

- Наблюдайте в консоли вебсервера входящие вебхуки сообщений

#### Запуск сервера из библиотеки

##### Подготовка среды

- [Пример подготовки среды сервера на операционной системе Ubuntu](serverUbuntu.md)

- [Пример подготовки среды сервера на операционной системе Windows](serverWindows.md)

##### Библиотека

- [Библиотека whatsapp-api-webhook-server-python](serverLibrary.md)

#### Запуск сервера в Docker

- [Пример разворачивания сервера в контейнере Docker](serverDocker.md)
- [Пример разворачивания сервера через Docker Compose](serverDockerCompose.md)
