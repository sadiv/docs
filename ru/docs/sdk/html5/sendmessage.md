# Как отправить текстовое сообщение из браузера
### Установка
```
<script type="text/javascript" src="https://unpkg.com/@green-api/whatsapp-api-client/lib/whatsapp-api-client.min.js"></script>
```
### Import 
Используя браузерный javascript 
```
<script src="https://unpkg.com/@green-api/whatsapp-api-client/lib/whatsapp-api-client.min.js"></script>
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

Комплексный пример отправки сообщений и получения уведомлений из браузера| [browserExample.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExample.html)

#### Как отправить текстовое сообщения на номер WhatsApp

Используя  js script
``` 
<script src="https://unpkg.com/@green-api/whatsapp-api-client/lib/whatsapp-api-client.min.js"></script>
<script>
    const restAPI = whatsAppClient.restAPI(({
        idInstance: "YOUR_ID_INSTANCE",
        apiTokenInstance: "YOUR_API_TOKEN_INSTANCE"
    }))
    restAPI.message.sendMessage("79999999999@c.us", null, "hello world")
    .then((data) => {
        console.log(data);
    }).catch((reason) =>{
        console.error(reason);
    });
</script>
```
### Полный список примеров

Описание |  Модуль
----- | ----- 
Комплексный пример отправки сообщений и получения уведомлений из браузера| [browserExample.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExample.html)
Пример получения QR кода по HTTP | [browserExampleQRCode.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExampleQRCode.html)
Пример получения QR кода по websocket| [browserExampleQRCodeWebsocket.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExampleQRCodeWebsocket.html)