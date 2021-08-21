# SendFileByUrl

Метод предназначен для отправки файла, загружаемого по ссылке.
Сообщение будет добавлено в очередь на отправку.
Скорость отправки сообщений из очереди регулирует параметр [Интервал отправки сообщений](../send-messages-delay.md).

Файлы видео, аудио и изображений отправляются как и в родном WhatsApp с возможностью просмотра и прослушки.
Документы отправляются так же как в родном WhatsApp.
Тип отправляемого файла и способ его отправки определяется по расширению файла.
Описание добавляется только к изображениям и видео.

> Максимальный размер отправляемых файлов равен 37 Мбайт.

## Запрос {#request}

Для отправки файла требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendFileByUrl/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](../chat-id.md)
`urlFile` | **string** | Да | Ссылка на отправляемый файл
`fileName` | **string** | Да | Название файла. Должно содержать расширение файла
`caption` | **string** | Нет | Описание под файлом. Описание добавляется к видео, изображениям.
`quotedMessageId` | **string** | Нет | Идентификатор цитируемого сообщения,если указан то сообщение отправится с цитированием указанного сообщения чата

### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "chatId": "79001234567@c.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Лошадка"
}
```

Отправка сообщения в групповой чат:
```json
{
    "chatId": "79001234567-1581234048@g.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Лошадка"
}
```

Отправка сообщения с цитированием:
```json
{
    "chatId": "79001234567@с.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Лошадка",
    "quotedMessageId": "361B0E63F2FDF95903B6A9C9A102F34B"
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

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendFileByUrl/{{apiTokenInstance}}"

payload = "{\r\n   \t\"chatId\": \"79001234567@c.us\",\r\n\t\"urlFile\": \"https://avatars.mds.yandex.net/get-pdb/477388/77f64197-87d2-42cf-9305-14f49c65f1da/s375\",\r\n\t\"fileName\": \"horse.png\",\r\n\t\"caption\": \"лошадка\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```