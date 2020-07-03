# Scanqrcode

Метод предназначен для сканирования QR кода для авторизации аккаунта Whatsapp.
Аккаунт WhatsApp должен быть в неавторизованном состоянии, если он не новый, нужно предварительно разлогинить аккаунт методом logout.

Необходимо установить websocket соединение по адресу: {{host-websocket}}/waInstance{{idInstance}}/scanqrcode/{{apiTokenInstance}

Например: wss://api.green-api.com/waInstance123/scanqrcode/7716c760bb1b9853bcc126bc1b133fac489ccf1b3dc969d4b1

Авторизовать аккаунт можно по ссылке вида: {{host}}/waInstance{{idInstance}}/{{apiTokenInstance}}

Например: https://api.green-api.com/waInstance123/7716c760bb1b9853bcc126bc1b133fac489ccf1b3dc969d4b1

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | Тип сообщения, возможные значения qrCode || error || accountData || alreadyLogged || timeoutExpired
`message` | **string** | Содержание сообщения 
| | если type=qrCode, message=изображение QR кода в base64 кодировке. Для вывода в браузере нужно добавить "data:image/png;base64, {message}";
| | если type=error, message=описание ошибки;
| | если type=alreadyLogged значит аккаунт Whatsapp уже авторизован, вызов QR кода невозможен;
| | если type=timeoutExpired значит стекло время за которое QR код должен был отсканирован;
`wid` | **string** | Идентификатор аккаунта в формате Whatsapp, когда type=accountData;
`pushname` | **string** | Имя аккаунта в Whatsapp, когда type=accountData
`proxy` | **string** |  ip адрес закрепленного прокси за аккаунтом, когда type=accountData
`webhookUrl` | **string** | URL для получения webhook уведомлений, когда type=accountData
