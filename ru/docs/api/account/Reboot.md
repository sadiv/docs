# Reboot

Метод предназначен для перезагрузки (перезапуска) аккаунта Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Отсутствуют

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`isReboot` | **boolean** | Результат перезапуска аккаунта Whatsapp

### Пример тела ответа {#response-example-body}

```json
{
    "isReboot": true
}
```

### Ошибки Reboot {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/reboot/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```