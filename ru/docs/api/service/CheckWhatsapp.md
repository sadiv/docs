# CheckWhatsapp

Метод проверяет наличие аккаунта Whatsapp на номере телефона

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`phoneNumber` | **integer** | Да | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`

### Пример тела запроса {#request-example-body}

```json
{
    "phoneNumber": 79001234567
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`existsWhatsapp` | **boolean** | Флаг наличия Whatsapp на номере телефона

### Пример тела ответа {#response-example-body}

```json
{
    "existsWhatsapp": true
}
```

### Ошибки CheckWhatsapp {#errors}

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.
400 | `bad phone number, valid 11 or 12 digits` | Неверный формат номера телефона, должен быть 11 или 12 цифр
400 | `check phone number timeout limit exceeded` | Превышен лимит времени ожидания ответа о проверке номера телефона

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/checkWhatsapp/{{apiTokenInstance}}"

payload = "{\r\n    \"phoneNumber\": 79001234567\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```