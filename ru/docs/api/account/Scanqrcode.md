# Scanqrcode

Метод предназначен для сканирования QR-кода для авторизации аккаунта.
Аккаунт должен быть в неавторизованном состоянии. Если аккаунт авторизован, то предварительно требуется разлогинить аккаунт методом [Logout](Logout.md).

Необходимо установить websocket соединение по адресу: 

```
wss://api.green-api.com/waInstance{{idInstance}}/scanqrcode/{{apiTokenInstance}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | Тип сообщения, возможные значения qrCode, error, accountData, alreadyLogged, timeoutExpired
`message` | **string** | Содержание сообщения 
| | если type=qrCode, message=изображение QR кода в base64 кодировке. Для вывода в браузере нужно добавить "data:image/png;base64, {message}";
| | если type=error, message=описание ошибки;
| | если type=alreadyLogged значит аккаунт WhatsApp уже авторизован, вызов QR кода невозможен;
| | если type=timeoutExpired значит стекло время за которое QR код должен был отсканирован;
`wid` | **string** | Идентификатор аккаунта в формате WhatsApp, когда type=accountData;
`pushname` | **string** | Имя аккаунта в WhatsApp, когда type=accountData
`proxy` | **string** |  ip адрес закрепленного прокси за аккаунтом, когда type=accountData
`webhookUrl` | **string** | URL для получения webhook уведомлений, когда type=accountData
