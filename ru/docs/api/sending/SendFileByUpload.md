# SendFileByUpload

Метод предназначен для отправки файла, загружаемого через форму (form-data).
Размер принимаемых файлов ограничен 37 мегабайтами.
Сообщение будет добавлено в очередь на отправку.
Файлы видео, аудио и изображений отправляются как и в родном Whatsapp с возможностью просмотра и прослушки.
Документы отправляются так же как в родном Whatsapp.
Тип отправляемого файла и способ его отправки определяется по расширению файла.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](/api/chat-id)
`caption` | **string** | Нет | Описание под файлом. Описание добавляется к видео, изображениям и документам
`file` | **file** | Да | Отправляемый файл

### Пример тела запроса {#request-example-body}

Пример кода на Python

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendFileByUpload/{{apiTokenInstance}}"

payload = {'chatId': '79001234567@c.us',
'caption': 'Описание'}
files = [
  ('file', open('/C:/window.jpg','rb'))
]
headers= {}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

print(response.text.encode('utf8'))
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

### Ошибки SendFileByUpload {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)
