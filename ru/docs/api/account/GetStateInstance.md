# GetStateInstance

Метод предназначен для получения состояния аккаунта.

## Запрос {#request}

Для получения состояния аккаунта требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetStateInstance/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`stateInstance` | **string** | Состояние авторизации аккаунта, возможные варианты: notAuthorized - аккаунт не авторизован, authorized - аккаунт авторизован, sleepMode - аккаунт в спящем режиме (когда устройство, на котором работает приложение WhatsApp, выключено)

### Пример тела ответа {#response-example-body}

```json
{
    "stateInstance": "authorized"
}
```

### Ошибки GetStateInstance {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getStateInstance/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```