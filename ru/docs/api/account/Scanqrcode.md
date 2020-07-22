# Получить QR-код через websocket

Наравне с получением QR-кода методом [QR](QR.md) существует возможность получить QR-код через websocket-соединение.
Для этого требуется установить websocket-соединение по адресу: 

```
wss://api.green-api.com/waInstance{{idInstance}}/scanqrcode/{{apiTokenInstance}
```

## Ответ {#response}

Поля ответа аналогичные методу [QR](QR.md#response-parameters)

