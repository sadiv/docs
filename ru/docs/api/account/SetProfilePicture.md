# SetProfilePicture

Метод предназначен для установки аватара аккаунта.

## Запрос {#request}

Для установки аватара аккаунта требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/setProfilePicture/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`file` | **file** | Да | Отправляемый файл в формате *.jpg

### Пример тела запроса {#request-example-body}

Пример кода на Python

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setProfilePicture/{{apiTokenInstance}}"

payload={}
files=[
  ('file',('{{file}}.jpeg',open('/C:/{{file}}.jpeg','rb'),'image/jpeg'))
]
headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`setProfilePicture` | **boolean** | флаг результата установки аватара 
`urlAvatar` | **string** | url установленного аватара 
`reason` | **string** | Причина почему аватар не был установлен 

### Пример тела ответа {#response-example-body}

В случае успеха, в ответ на запрос, отдается JSON строка следующего вида с HTTP статусом 200:

```json
{
    "setProfilePicture": true,
    "urlAvatar": "https://pps.whatsapp.net/v/t61.24******-24/23**********_********23704_************77468_n.jpg?ccb=11-4&oh=**********b6ccc377d6332abad7d0bb&oe=********"
}
```

### Ошибки SetProfilePicture {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)