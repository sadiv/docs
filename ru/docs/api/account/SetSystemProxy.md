# SetSystemProxy

Метод предназначен для установки системного прокси. Используйте метод, когда требуется сбросить пользовательские настройки прокси на системные.

## Запрос {#request}

Для установки системного прокси требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/SetSystemProxy/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`setSystemProxy` | **boolean** | Флаг установки системного прокси: `true` - системный прокси установлен; `false` - не установлен

### Пример тела ответа {#response-example-body}

```json
{
    "setSystemProxy": true
}
```

### Ошибки SetSystemProxy {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/SetSystemProxy/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```