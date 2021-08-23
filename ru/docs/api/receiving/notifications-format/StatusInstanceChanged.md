# Статус сокета аккаунта

Входящее уведомление данного типа содержит данные о состоянии сокета (готов или нет инстанс отправлять/принимать сообщения)

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | [Тип входящего уведомления](type-webhook.md). Для уведомлений данного типа поле принимает значение `statusInstanceChanged`
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX-формате
`statusInstance` | **string** | Состояние аккаунта. Принимает значения:
| | `online` - Аккаунт может принимать/отправлять сообщения, сокет открыт
| | `offline` - Аккаунт не может принимать/отправлять сообщения, сокет закрыт

Поля объекта `instanceData`

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате WhatsApp
`typeInstance` | **string** | Тип мессенджера для аккаунта

### Пример тела уведомления {#webhook-example-body}

```json
{
    "typeWebhook":"statusInstanceChanged",
    "instanceData": {
        "idInstance": 1,
        "wid": "79001234567@c.us",
        "typeInstance":"whatsapp"
    },
    "timestamp": 1586700690,
    "statusInstance": "online"
}
```
