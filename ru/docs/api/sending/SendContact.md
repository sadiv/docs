# SendContact

Метод предназначен для отправки сообщения с контактом.
Формируется визитная карточка контакта и отправляется в чат.
Сообщение будет добавлено в очередь на отправку.
Скорость отправки сообщений из очереди регулирует параметр [Интервал отправки сообщений](../send-messages-delay.md).

## Запрос {#request}

Для отправки сообщения с контактом требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/sendContact/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](../chat-id.md)
`contact` | **object** | Да | Объект о контакте
`quotedMessageId` | **string** | Нет | Идентификатор цитируемого сообщения,если указан то сообщение отправится с цитированием указанного сообщения чата

Параметры объекта `contact`:

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`phoneContact ` | **integer** | Да | номер телефона контакта в международном формате (без +) 11 или 12 цифр
`firstName` | **string** | Если не указаны `middleName`, `lastName`, `company` | Имя контакта
`middleName` | **string** | Если не указаны `firstName`, `lastName`, `company` | Отчество контакта
`lastName` | **string** | Если не указаны `middleName`, `firstName`, `company` | Фамилия контакта
`company` | **string** | Если не указаны `middleName`, `lastName`, `firstName` | Название компании контакта

### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "chatId": "79001234567@c.us",
    "contact": {
        "phoneContact": 79001234568,
        "firstName": "Артем",
        "middleName": "Петрович",
        "lastName": "Евпаторийский",
        "company": "Велосипед"
    }
}
```

Отправка сообщения в групповой чат:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "contact": {
        "phoneContact": 79001234568,
        "firstName": "Артем",
        "middleName": "Петрович",
        "lastName": "Евпаторийский",
        "company": "Велосипед"
    }
}
```

Отправка сообщения с цитированием:
```json
{
    "chatId": "79001234567@c.us",
    "quotedMessageId": "361B0E63F2FDF95903B6A9C9A102F34B",
    "contact": {
        "phoneContact": 79001234568,
        "firstName": "Артем",
        "middleName": "Петрович",
        "lastName": "Евпаторийский",
        "company": "Велосипед"
    }
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

### Ошибки SendContact {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendContact/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"79001234567@c.us\",\r\n\t\"contact\": {\r\n\t\t\"phoneContact\": 79001234568,\r\n    \t\"firstName\": \"Артем\",\r\n\t\t\"middleName\": \"Петрович\",\r\n\t\t\"lastName\": \"Евпаторийский\",\r\n\t\t\"company\": \"Велосипед\"\r\n\t}\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```