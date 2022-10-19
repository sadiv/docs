# NodeJs WhatsApp Library
* [![build](https://github.com/green-api/whatsapp-api-client/workflows/build_library/badge.svg)](https://github.com/green-api/whatsapp-api-client/actions/workflows/build_library.yml)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/green-api/whatsapp-api-client/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/green-api/whatsapp-api-client.svg)](https://github.com/green-api/whatsapp-api-client/releases)

[Javascript библиотека](https://github.com/green-api/whatsapp-api-client-js) для интеграции с мессенджером WhatsAPP через API сервиса [green-api.com](https://green-api.com). Чтобы воспользоваться библиотекой нужно получить регистрационный токен и id аккаунта в [личном кабинете](https://console.green-api.com). Есть бесплатный тариф аккаунта разработчика.

#### API

Документация к REST API находится по [ссылке](https://green-api.com/docs/api/). Библиотека является оберткой к REST API, поэтому документация по ссылке выше применима и к самой библиотеке.

#### Авторизация 

Чтобы отправить сообщение или выполнить другой метод Green-API, аккаунт WhatsApp в приложении телефона должен быть в авторизованном состоянии. Для авторизации аккаунта перейдите в [личный кабинет](https://console.green-api.com) и сканируйте QR-код с использованием приложения WhatsApp.

#### [Как отправить текстовое сообщение](sendmessage.md)
#### [Как отправить файл по ссылке](sendfilebyurl.md)
#### [Как отправить файл загрузкой с диска](sendfilebyupload.md)
#### [Как принять и обработать уведомление](receiveNotification.md)
#### [Как принять и обработать уведомления используя сервер](receiveNotificationserver.md)
#### [Как получить QR код](getqr.md)

#### Разворачивание окружения разработки

1. Склонируйте репозиторий через ``git clone``
2. Установите зависимости через ``npm install``
3. Установите глобально библиотеку ``rollup`` для сборки.
4. Для вебхуков добавьте `express` как новую зависимость через npm
5. Создайте файл `.env` в рутовом каталоге и пропишите переменные окружения. Образец переменных в файле [env.example](https://github.com/green-api/whatsapp-api-client-js/blob/master/env.example)

#### Сборка
Скомпилировать как browser, так и node/webpack версии либы можно одной командой
```
npm run build
```
#### Документация по методам сервиса

[Документация по методам сервиса](https://green-api.com/docs/api/)

#### Сторонние продукты

* [axios](https://github.com/axios/axios) - для http запросов
* [express](https://www.npmjs.com/package/express) - сервер приложений для вебхуков

#### Лицензия

Лицензировано на условиях MIT. Смотрите файл [LICENSE](https://github.com/green-api/whatsapp-api-client-python/blob/master/LICENSE)
