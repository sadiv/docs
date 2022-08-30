# CheckWhatsapp

Метод проверяет наличие аккаунта WhatsApp на номере телефона.

## Запрос {#request}

Для проверки наличия аккаунта WhatsApp требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/CheckWhatsapp/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

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
`existsWhatsapp` | **boolean** | Флаг наличия WhatsApp на номере телефона

### Пример тела ответа {#response-example-body}

```json
{
    "existsWhatsapp": true
}
```

### Ошибки CheckWhatsapp {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `bad phone number, valid 11 or 12 digits` | Неверный формат номера телефона, должен быть 11 или 12 цифр
400 | `check phone number timeout limit exceeded` | Превышен лимит времени ожидания ответа о проверке номера телефона

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/checkWhatsapp/{{apiTokenInstance}}"

payload = "{phoneNumber: 79001234567}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```