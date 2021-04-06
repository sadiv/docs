# Входящий звонок

Уведомление данного типа возникает при входящем звонке и содержит информацию об инициаторе и адресате звонка.

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`from` | **string** | [Идентификатор](../../../chat-id.md#corr) инициатора звонка
`typeWebhook` | **string** | [Тип входящего уведомления](type-webhook.md). Для уведомлений данного типа поле принимает значение `incomingCall`
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX-формате
`idMessage` | **string** | Идентификатор входящего звонка


Поля объекта `instanceData`

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате WhatsApp
`typeInstance` | **string** | Тип мессенджера для аккаунта

### Пример тела уведомления {#webhook-example-body}

```json
{
    "from": "79001234500@c.us",
    "typeWebhook": "incomingCall",
    "instanceData": {
        "idInstance": 1234,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
     "timestamp": 1617691757,
     "idMessage": "104179EDB7F5328988D8834107EEBE50"
}
```