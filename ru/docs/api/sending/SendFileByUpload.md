# SendFileByUpload

Метод предназначен для отправки файла, загружаемого через форму (form-data).
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
POST https://api.green-api.com/waInstance{{idInstance}}/SendFileByUpload/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](../chat-id.md)
`file` | **file** | Да | Отправляемый файл
`caption` | **string** | Нет | Описание под файлом. Описание добавляется к видео, изображениям.

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

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)
