# Статус аккаунта

Webhook уведомление данного типа содержит данные о состоянии авторизации аккаунта

## webhook {#webhook}

### Поля webhook {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | [Тип webhook уведомления](type-webhook). Для уведомлений данного типа поле принимает значение `stateInstanceChanged`
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX-формате
`stateInstance` | **string** | Состояние аккаунта. Принимает значения:
| | `notAuthorized` - Аккаунт не авторизован. Для авторизации аккаунта обратитесь к разделу [Перед началом работы](../../../before-start#qr)
| | `authorized` - Аккаунт авторизован
| | `sleepMode` - Аккаунт ушел в спящий режим, возможен когда выключен телефон. После включения телефона может потребоваться до 5 минут для перевода состояния аккаунта в значение `authorized`.

Поля объекта `instanceData`

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате WhatsApp
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
