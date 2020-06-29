# OutgoingMessageStatus

Получен статус отправленного исходящего сообщения или файла

## webhook {#webhook}

### Поля webhook {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | Тип webhook уведомления. Возможные варианты stateInstanceChanged, outgoingMessageStatus, incomingMessageReceived, deviceInfo. В данном случае поле равняется outgoingMessageStatus.
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX формате
`idMessage` | **string** | Идентификатор исходящего сообщения или файла, отправленного методами sendMessage, sendFileByUrl, sendFileByUpload, sendLocation, sendContact, sendLink
`status` | **string** | Статус отправленного исходящего сообщения или файла, которое может принимать пять значений:
| | noAccount - нет аккаунта на номере телефона;
| | notInGroup - не состоите в данной группе;
| | sent - отправлено;
| | delivered - доставлено;
| | read - прочитано/просмотрено/прослушано

Поля объекта instanceData

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате Whatsapp
`typeInstance` | **string** | Тип мессенджера для аккаунта

### Пример тела webhook {#webhook-example-body}

```json
{
    "typeWebhook": "outgoingMessageStatus",
    "timestamp": 1586700802,
    "instanceData": {
        "idInstance": 1,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "idMessage": "3EB0608D6A2901063D63",
    "status": "noAccount"
}
```
