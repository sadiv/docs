# Как отправить файл загрузкой с диска
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

Полный пример можно посмотреть по ссылке: [SendWhatsAppFileUpload.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUpload.js)

#### Как отправить файл загрузкой с диска

``` js
import whatsAppClient from '@green-api/whatsapp-api-client'
import FormData from 'form-data'
import * as fs from 'fs'

(async () => {
    const restAPI = whatsAppClient.restAPI(({
        idInstance: process.env.ID_INSTANCE,
        apiTokenInstance: process.env.API_TOKEN_INSTANCE
    }))
    const data = new FormData();
    data.append('chatId', '7xxxxxxxxxx@c.us');
    data.append('caption', 'My file');
    data.append('file', fs.createReadStream('hello.txt'));
    const response = await restAPI.file.sendFileByUpload(data)
    console.log(`file uploaded ${response.idMessage}`)
})();
```
### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста используя Async| [SendWhatsAppMessageAsync.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageAsync.js)
Пример отправки текста используя Callback| [SendWhatsAppMessageCallback.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageCallback.js)
Пример отправки картинки по URL | [SendWhatsAppFileUrl.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUrl.js)
Пример отправки картинки загрузкой с диска | [SendWhatsAppFileUpload.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUpload.js)
Пример получения входящего уведомления методом receiveNotification| [ReceiveNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveNotifications.js)
Пример получения входящих уведомлений через webhook service REST API | [StartReceivingNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/StartReceivingNotifications.js)
Пример получения входящих уведомлений на сервер| [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)
Пример получения QR кода по HTTP | [getQRCode.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCode.js)
Пример получения QR кода по websocket| [getQRCodeWebsocket.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCodeWebsocket.js)