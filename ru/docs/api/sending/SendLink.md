# SendLink

Метод предназначен для отправки сообщения со ссылкой, по которой будут добавлены превью изображения, заголовок и описание.
Картинка, заголовок и описание получаются из [Open Graph](https://en.wikipedia.org/wiki/Facebook_Platform#Open_Graph_protocol) разметки страницы, на которую указывает ссылка.
Сообщение будет добавлено в очередь на отправку. Скорость отправки сообщений из очереди регулирует параметр [Интервал отправки сообщений](../send-messages-delay.md).

## Запрос {#request}

Для отправки сообщения со ссылкой требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendLink/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](../chat-id.md)
`urlLink` | **string** | Да | Адрес ссылки

> Рекомендуется, чтобы страница, на которую указыает ссылка `urlLink` содержала разметку [Open Graph](https://en.wikipedia.org/wiki/Facebook_Platform#Open_Graph_protocol). В этом случае сообщение будет дополнено картинкой, заголовком и кратким описанием.

### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "chatId": "79001234567@c.us",
    "urlLink": "https://green-api.com"
}
```

Отправка сообщения в групповой чат:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "urlLink": "https://green-api.com"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | -----
`idMessage ` | **string** | Идентификатор отправленного сообщения 

### Пример тела ответа {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Ошибки SendLink {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLink/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"urlLink\": \"https://green-api.com\"\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
