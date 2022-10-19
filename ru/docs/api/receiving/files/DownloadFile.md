# DownloadFile

Метод предназначен для скачивания принятых и отправленных файлов.
Ссылки на принятые файлы передаются во [Входящих сообщениях](../notifications-format/incoming-message/Webhook-IncomingMessageReceived.md), а также их можно получить методом [LastIncomingMessages](../../../api/journals/LastIncomingMessages.md).
Ссылки на отправленные файлы можно получить методом [LastOutgoingMessages](../../../api/journals/LastOutgoingMessages.md).

> Срок хранения файлов и соответственно возможность их первоначального скачивания ограничено временем, которое хранит их у себя WhatsApp

## Запрос {#request}

```
POST https://api.green-api.com/waInstance{{idInstance}}/downloadFile/{{apiTokenInstance}}
```

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор личного или группового чата](../chat-id.md) историю сообщений которого требуется получить
`idMessage ` | **string** | Да | Идентификатор сообщения

## Ответ {#response}

Файл из сообщения

### Ошибки DownloadFile {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../../common-errors.md)

## Пример кода на curl  {#request-example-curl}

```
curl --location -g --request POST '{{host}}/waInstance{{idInstance}}/downloadEncFile/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "79000001234@c.us",
    "idMessage": "A322F800D3F12CD4858CC947DAFB77A2"
}'
```

## Пример кода на python  {#request-example-python}

```
import requests
import json

url = "{{host}}/waInstance{{idInstance}}/downloadFile/{{apiTokenInstance}}"

payload = json.dumps({
  "chatId": "790000312312@c.us",
  "idMessage": "A322F800D3F12CD4858CC947DAFB77A2"
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```