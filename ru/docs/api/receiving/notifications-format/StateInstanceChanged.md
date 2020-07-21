# Статус аккаунта

Входящее уведомление данного типа содержит данные о состоянии авторизации аккаунта

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | [Тип входящего уведомления](type-webhook.md). Для уведомлений данного типа поле принимает значение `stateInstanceChanged`
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX-формате
`stateInstance` | **string** | Состояние аккаунта. Принимает значения:
| | `notAuthorized` - Аккаунт не авторизован. Для авторизации аккаунта обратитесь к разделу [Перед началом работы](../../../before-start.md#qr)
| | `authorized` - Аккаунт авторизован
| | `sleepMode` - Аккаунт ушел в спящий режим. Состояние возможно, когда выключен телефон. После включения телефона может потребоваться до 5 минут для перевода состояния аккаунта в значение `authorized`.

Поля объекта `instanceData`

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате WhatsApp
`typeInstance` | **string** | Тип мессенджера для аккаунта

### Пример тела уведомления {#webhook-example-body}

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
