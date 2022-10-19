# SetGroupPicture

Метод устанавливает аватар группы.

## Запрос {#request}

Для установки аватара группового чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/setGroupPicture/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`file` | **file** | Да | Отправляемый файл в формате *.jpg
`groupId` | **string** | Да | [Идентификатор группового чата](../chat-id.md#gus)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setGroupPicture/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"120363043968066561@g.us\",\r\n}"
files=[
  ('file',('{{file}}.jpeg',open('/C:/{{file}}.jpeg','rb'),'image/jpeg'))
]
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload, files=files)

print(response.text.encode('utf8'))
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`setGroupPicture` | **boolean** | флаг результата установки аватара группы
`urlAvatar` | **string** | url  на установленное изображение
`reason` | **string** | причина почему аватар не был установлен

### Пример тела ответа {#response-example-body}

```json
{
    "setGroupPicture": true,
    "urlAvatar": "https://pps.whatsapp.net/v/t61.24694-24/138639660_724754321806449_9118612187814397965_n.jpg?oh=997b0bb13b6bbb750432a86d4b8d935d&oe=600****BB4",
	"reason": ""
}

```

### Ошибки SetGroupPicture {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

