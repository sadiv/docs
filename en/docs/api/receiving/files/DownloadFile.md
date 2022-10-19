# DownloadFile

The method is aimed for downloading incoming and outgoing files.
Links to incoming files are transmitted in [Incoming messages](../notifications-format/incoming-message/Webhook-IncomingMessageReceived.md), and you can also get them using [LastIncomingMessages](../../../api/journals/LastIncomingMessages.md) method.
You can get links to outgoing files using [LastOutgoingMessages](../../../api/journals/LastOutgoingMessages.md) method.

> Files storage period and, accordingly, the capability to download them is limited by WhatsApp

## Request {#request}

```
POST https://api.green-api.com/waInstance{{idInstance}}/downloadFile/{{apiTokenInstance}}
```

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Chat id](../chat-id.md),  for example 7900023125@c.us 
`idMessage` | **string** | Yes | Message Id transmitted in [Incoming messages](../notifications-format/incoming-message/Webhook-IncomingMessageReceived.md) or when sending files using [SendFileByUrl](../../../api/sending/SendFileByUrl.md), [SendFileByUpload](../../../api/sending/SendFileByUpload.md) methods. This parameter is transmitted as the final part of the url request

## Response {#response}

File from message

### DownloadFile errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../../common-errors.md) section

## Curl example  {#request-example-python}
```
curl --location -g --request POST '{{host}}/waInstance{{idInstance}}/downloadEncFile/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "79000001234@c.us",
    "idMessage": "A322F800D3F12CD4858CC947DAFB77A2"
}'
```
