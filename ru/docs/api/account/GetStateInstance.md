# GetStateInstance

Метод предназначен для получения состояния аккаунта Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Отсутствуют

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`stateInstance` | **string** | Состояние авторизации аккаунта, возможные варианты: notAuthorized - аккаунт не авторизован, authorized - аккаунт авторизован, sleepMode - аккаунт в спящем режиме (когда устройство, на котором работает приложение Whatsapp, выключено)

### Пример тела ответа {#response-example-body}

```json
{
    "stateInstance": "authorized"
}
```

### Ошибки GetStateInstance {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getStateInstance/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```