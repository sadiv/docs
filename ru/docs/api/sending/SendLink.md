# SendLink

Метод предназначен для отправки сообщения со ссылкой, по которой будут добавлены превью изображения, заголовок и описание.
Картинка, заголовок и описание получаются из Open Graph разметки страницы, на которую указывает ссылка.
Сообщение будет добавлено в очередь на отправку.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Если не указан `phoneNumber` | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`phoneNumber` | **integer** | Если не указан `chatId` | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`
`urlLink` | **string** | Да | Адрес ссылки

### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "phoneNumber": 79001234567,
    "urlLink": "https://my.site.com"
}
```

Отправка сообщения в группу:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "urlLink": "https://my.site.com"
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

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLink/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"\",\r\n\t\"phoneNumber\": 79001234567,\r\n\t\"urlLink\": \"https://my.site.com\"\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
