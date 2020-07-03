# GetDeviceInfo

Метод предназначен для получения информации об устройстве на котором запущено приложение Whatsapp

## Запрос {#request}

### Параметры запроса {#request-parameters}

Отсутствуют

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`platform` | **string** | Операционная система устройства на котором запущено приложение Whatsapp
`deviceManufacturer` | **string** | Производитель устройства
`deviceModel` | **string** | Модель устройства
`osVersion` | **string** | Версия операционной системы
`waVersion` | **string** | Версия приложения Whatsapp
`battery` | **integer** | Уровень заряда батареи

### Пример тела ответа {#response-example-body}

```json
{
    "platform": "iphone",
    "deviceManufacturer": "Apple",
    "deviceModel": "iPhone 11",
    "osVersion": "13.4.1",
    "waVersion": "2.20.42",
    "battery": 90
}
```

### Ошибки GetDeviceInfo {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getDeviceInfo/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```