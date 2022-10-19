# Как отправить файл по ссылке
### Установка
```
npm i @green-api/whatsapp-api-client
```
### Import 
Есть несколько способов импортировать библиотеку в проект
Используя классический javascript 
```
const whatsAppClient = require("@green-api/whatsapp-api-client");
```
Используя ES6 javascript 
```
import whatsAppClient from "@green-api/whatsapp-api-client";
```
Используя typescript 
```ы
import * as whatsAppClient from "@green-api/whatsapp-api-client";
```
#### Как инициализировать объект

Храните Ваши авторизационные данные отдельно от кода. Библиотека позволяет создать  файл с произвольным именем и местом в следующем формате: 
```
API_TOKEN_INSTANCE = "MY_API_TOKEN_INSTANCE"
ID_INSTANCE = "MY_ID_INSTANCE"
```
Передать ключи, можно используя пример ниже:
``` js
const restAPI = whatsAppClient.restAPI(({
    credentialsPath: "examples\\credentials"
}))
```
### Примеры

Полный пример можно посмотреть по ссылке: [SendWhatsAppFileUrl.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUrl.js)

#### Как отправить файл по ссылке

``` js
import whatsAppClient from '@green-api/whatsapp-api-client'

(async () => {
    const restAPI = whatsAppClient.restAPI(({
        idInstance: YOUR_ID_INSTANCE,
        apiTokenInstance: YOUR_API_TOKEN_INSTANCE
    }))
    const response = await restAPI.file.sendFileByUrl("79999999999@c.us", null, 'https://avatars.mds.yandex.net/get-pdb/477388/77f64197-87d2-42cf-9305-14f49c65f1da/s375', 'horse.png', 'horse');
})();
```
### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста используя Async| [SendWhatsAppMessageAsync.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageAsync.js)
Пример отправки текста используя Callback| [SendWhatsAppMessageCallback.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageCallback.js)
Пример отправки картинки по URL | [SendWhatsAppFileUrl.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUrl.js)
Пример отправки картинки загрузкой с диска | [SendWhatsAppFileUpload.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUpload.js)
Пример получения входящего уведомления методом receiveNotification| [ReceiveNotifications.js](ReceiveNotifications.js)
Пример получения входящих уведомлений через webhook service REST API | [StartReceivingNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/StartReceivingNotifications.js)
Пример получения входящих уведомлений на сервер| [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)
Пример получения QR кода по HTTP | [getQRCode.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCode.js)
Пример получения QR кода по websocket| [getQRCodeWebsocket.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCodeWebsocket.js)