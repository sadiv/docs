# Reboot

Метод предназначен для перезапуска аккаунта.

## Запрос {#request}

Для перезапуска аккаунта требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/Reboot/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](/before-start#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`isReboot` | **boolean** | Результат перезапуска аккаунта WhatsApp

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