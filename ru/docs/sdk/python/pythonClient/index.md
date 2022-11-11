# Python WhatsApp client Library

[![Python application](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-app.yml/badge.svg)](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-app.yml)
[![Upload Python Package](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-publish.yml/badge.svg)](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-publish.yml)

[Python библиотека](https://github.com/green-api/whatsapp-api-client-python) для интеграции с мессенджером WhatsAPP через API сервиса [green-api.com](https://green-api.com). Чтобы воспользоваться библиотекой нужно получить регистрационный токен и id аккаунта в [личном кабинете](https://console.green-api.com). Есть бесплатный тариф аккаунта разработчика.

#### API

Документация к REST API находится по [ссылке](https://green-api.com/docs/api/). Библиотека является оберткой к REST API, поэтому документация по ссылке выше применима и к самой библиотеке.

#### Авторизация 

Чтобы отправить сообщение или выполнить другой метод Green-API, аккаунт WhatsApp в приложении телефона должен быть в авторизованном состоянии. Для авторизации аккаунта перейдите в [личный кабинет](https://console.green-api.com) и сканируйте QR-код с использованием приложения WhatsApp.

#### [Как отправить текстовое сообщение](sendmessage.md)
#### [Как отправить файл по ссылке](sendfilebyurl.md)
#### [Как отправить файл загрузкой с диска](sendfilebyupload.md)
#### [Как создать группу и отправить в неё сообщение](creategroup.md)
#### [Как обрабатывать входящие уведомления](startReceiveNotification.md)
#### [Полный список методов библиотеки](fullmethods.md)

#### Документация по методам сервиса

[Документация по методам сервиса](https://green-api.com/docs/api/)

#### Сторонние продукты

- [requests](https://requests.readthedocs.io) - для http запросов

#### Лицензия

Лицензировано на условиях MIT. Смотрите файл [LICENSE](https://github.com/green-api/whatsapp-api-client-python/blob/master/LICENSE)
