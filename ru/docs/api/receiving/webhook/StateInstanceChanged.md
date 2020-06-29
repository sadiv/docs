# StateInstanceChanged

Изменено состояние авторизации аккаунта

## webhook {#webhook}

### Поля webhook {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | Тип webhook уведомления. Возможные варианты stateInstanceChanged, outgoingMessageStatus, incomingMessageReceived, deviceInfo. В данном случае поле равняется stateInstanceChanged.
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX формате
`stateInstance` | **string** | Может принимать три значения:
| | notAuthorized - аккаунт не авторизован;
| | authorized - аккаунт авторизован;
| | sleepMode - аккаунт ушел в спящий режим, возможен когда выключен телефон

Поля объекта instanceData

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате Whatsapp
`typeInstance` | **string** | Тип мессенджера для аккаунта

### Пример тела webhook {#webhook-example-body}

```json
{
    "typeWebhook":"stateInstanceChanged",
    "instanceData": {
        "idInstance": 1,
        "wid": "79001234567@c.us",
        "typeInstance":"whatsapp"
    },
    "timestamp": 1586700690,
    "stateInstance": "notAuthorized"
}
```
