# QR

Метод предназначен для получения QR-кода. 
Для авторизации аккаунта требуется считать QR-код из приложения [WhatsApp Business](https://www.whatsapp.com/business/) на телефоне.
Также получить QR-код и авторизовать аккаунт можно в личном кабинете. Процедура авторизации аккаунта через личный кабинет описана в разделе [Перед началом работы](../../before-start.md#qr).

> QR-код обновляется каждые 20 сек., поэтому вызывать метод получения QR-кода рекомендуется с интервалом в 5 сек.

Для получения QR-кода аккаунт должен быть в неавторизованном состоянии. Если аккаунт авторизован, то предварительно требуется разлогинить аккаунт методом [Logout](Logout.md).

После успешного сканирования QR-кода и авторизации аккаунта формируется [входящее уведомление](../receiving/index.md) с видом [Статус аккаунта](../receiving/notifications-format/StateInstanceChanged.md).

> Также получить QR-код можно через [websocket-соединение](Scanqrcode.md) 

## Запрос {#request}

Для получения QR-кода требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/qr/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).


## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | Тип сообщения, возможные значения `qrCode`, `error`, `alreadyLogged`
`message` | **string** | Содержание сообщения. Принимает различные значения в зависимости от значения поля `type`


#### Получено изображение QR-кода {#response-type-qrCode}

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | `qrCode` - получено изображение QR-кода
`message` | **string** | Изображение QR-кода в кодировке `base64`. Для вывода в браузере нужно добавить строку `data:image/png;base64, {message}`


#### Возникла ошибка {#response-type-error}

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | `error` - возникла ошибка
`message` | **string** | Описание ошибки


#### Аккаунт уже авторизован {#response-type-alreadyLogged}

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | `alreadyLogged` - аккаунт уже авторизован. Для получения QR-кода требуется предварительно разлогинить аккаунт методом [Logout](Logout.md)
`message` | **string** | Принимает значение `instance account already authorized`


### Ошибки QR {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример получения QR-кода в браузере {#request-example-js}

```js
// ...
```

Также пример получения QR-кода в браузере можно посмотреть в файле [browserExample](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExample.html) 

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/qr/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
