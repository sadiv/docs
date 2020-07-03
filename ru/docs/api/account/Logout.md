# Logout

Метод предназначен для разлогинивания аккаунта Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Отсутствуют

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`isLogout` | **boolean** | Результат разлогинивания аккаунта Whatsapp

### Пример тела ответа {#response-example-body}

```json
{
    "isLogout": true
}
```

### Ошибки Logout {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/logout/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```