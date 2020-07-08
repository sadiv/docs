# DownloadFile

Метод предназначен для скачивания принятых и отправленных файлов.
Ссылки на принятые файлы передаются во [Входящих сообщениях](/api/receiving/webhook/incoming-message/Webhook-IncomingMessageReceived), а также их можно получить методом [LastIncomingMessages](/api/journals/LastIncomingMessages).
Ссылки на отправленные файлы можно получить методом [LastOutgoingMessages](/api/journals/LastOutgoingMessages).

> Срок хранения файлов и соответственно возможность их скачивания ограничено 24 часами.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`idMessage` | **string** | Да | Идентификатор сообщения, передаваемый во [Входящих сообщениях](/api/receiving/webhook/incoming-message/Webhook-IncomingMessageReceived) или при отправки файлов методами [SendFileByUrl](/api/sending/SendFileByUrl), [SendFileByUpload](/api/sending/SendFileByUpload). Данный параметр передаётся как завершающая часть url запроса

## Ответ {#response}

Файл из сообщения

### Ошибки DownloadFile {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/downloadFile/{{idMessage}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```