# SendFileByUrl

Метод предназначен для отправки файла, загружаемого по ссылке.
Размер загружаемого файла ограничен 37 мегабайтами.
Сообщение будет добавлено в очередь на отправку.
Файлы видео, аудио и изображений отправляются как и в родном Whatsapp с возможностью просмотра и прослушки.
Документы отправляются так же как в родном Whatsapp.
Тип отправляемого файла и способ его отправки определяется по расширению файла.


## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Если не указан `phoneNumber` | Идентификатор личного чата в формате `00000000000@c.us` или идентификатор группы в формате `00000000000-0000000000@g.us`; Пример: `79001234567@c.us` или `79001234567-1581234048@g.us`
`phoneNumber` | **integer** | Если не указан `chatId` | Номер телефона получателя в международном формате: 11 или 12 цифр; Пример: `79001234567` или `380123456789`
`urlFile` | **string** | Да | Ссылка на отправляемый файл
`fileName` | **string** | Да | Название файла. Должно содержать расширение файла
`caption` | **string** | Нет | Описание под файлом. Описание добавляется к видео, изображениям и документам

### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "phoneNumber": 79001234567,
    "urlFile": "https://my.site.com/img",
    "fileName": "horse.png",
    "caption": "Лошадка"
}
```

Отправка сообщения в группу:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "urlFile": "https://my.site.com/img",
    "fileName": "horse.png",
    "caption": "Лошадка"
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

### Ошибки SendFileByUrl {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendFileByUrl/{{apiTokenInstance}}"

payload = "{\r\n   \t\"chatId\": \"79001234567@c.us\",\r\n\t\"phoneNumber\": 79001234567,\r\n\t\"urlFile\": \"https://my.site.com/img\",\r\n\t\"fileName\": \"horse.png\",\r\n\t\"caption\": \"Лошадка\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```