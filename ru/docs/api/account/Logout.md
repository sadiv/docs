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

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/logout/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```