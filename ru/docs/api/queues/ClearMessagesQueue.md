# ClearMessagesQueue

Метод предназначен для очистки очереди сообщений на отправку.

## Запрос {#request}

Для очистки очереди сообщений требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/ClearMessagesQueue/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](/before-start#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`isCleared` | **boolean** | Флаг очистки очереди сообщений

### Пример тела ответа {#response-example-body}

```json
{
    "isCleared": true
}
```

### Ошибки ClearMessagesQueue {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/clearMessagesQueue/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```