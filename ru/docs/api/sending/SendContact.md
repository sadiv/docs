# SendContact

Метод предназначен для отправки сообщения с контактом.
Формируется визитная карточка контакта и отправляется в чат.
Сообщение будет добавлено в очередь на отправку.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Если не указан `phoneNumber` | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`phoneNumber` | **integer** | Если не указан `chatId` | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`
`contact` | **object** | Да | Объект о контакте

Параметры объекта contact:

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
    "phoneNumber": 79001234567,
    "contact": {
        "phoneContact": 79001234568,
        "firstName": "Артем",
        "middleName": "Петрович",
        "lastName": "Евпаторийский",
        "company": "Велосипед"
    }
}
```

Отправка сообщения в группу:
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

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendContact/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"\",\r\n\t\"phoneNumber\": 79001234567,\r\n\t\"contact\": {\r\n\t\t\"phoneContact\": 79001234568,\r\n    \t\"firstName\": \"Артем\",\r\n\t\t\"middleName\": \"Петрович\",\r\n\t\t\"lastName\": \"Евпаторийский\",\r\n\t\t\"company\": \"Велосипед\"\r\n\t}\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```