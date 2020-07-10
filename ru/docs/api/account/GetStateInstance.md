# GetStateInstance

Метод предназначен для получения состояния аккаунта.

## Запрос {#request}

Для получения состояния аккаунта требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetStateInstance/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`stateInstance` | **string** | Состояние аккаунта. Принимает значения:
| | `notAuthorized` - Аккаунт не авторизован. Для авторизации аккаунта обратитесь к разделу [Перед началом работы](../../before-start.md#qr)
| | `authorized` - Аккаунт авторизован
| | `sleepMode` - Аккаунт ушел в спящий режим. Состояние возможно, когда выключен телефон. После включения телефона может потребоваться до 5 минут для перевода состояния аккаунта в значение `authorized`.

### Пример тела ответа {#response-example-body}

```json
{
    "stateInstance": "authorized"
}
```

### Ошибки GetStateInstance {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getStateInstance/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```