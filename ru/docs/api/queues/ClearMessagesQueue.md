# ClearMessagesQueue

Метод предназначен для очистки очереди отправки сообщений

## Запрос {#request}

### Параметры запроса {#request-parameters}

Отсутствуют

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