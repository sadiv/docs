# GetStatusInstance

Метод предназначен для получения состояния сокета соединения инстанса аккаунта с WhatsApp.

## Запрос {#request}

Для получения состояния сокета аккаунта требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/getStatusInstance/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`statusInstance` | **string** | Состояние соединения сокета аккаунта. Принимает значения:
| | `online` - Аккаунт может принимать/отправлять сообщения, сокет открыт
| | `offline` - Аккаунт не может принимать/отправлять сообщения, сокет закрыт


### Пример тела ответа {#response-example-body}

```json
{
    "statusInstance": "online"
}
```

### Ошибки GetStatusInstance {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getStatusInstance/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```