# Типы входящих уведомлений

Входящие уведомления могут быть следующих типов:

- `stateInstanceChanged` - уведомление об изменении состояния авторизации аккаунта 
- `outgoingMessageStatus` - уведомление о статусах отправки/доставки/прочтении исходящих сообщений
- `incomingMessageReceived` - уведомление о входящих сообщениях и файлах
- `outgoingMessageReceived` - уведомление о сообщениях, отправленных с телефона вручную 
- `deviceInfo` - уведомление об устройстве (телефоне) и уровне заряда батареи

## Получение уведомлений разных типов
Для включения или отключения уведомлений по типам используйте метод [SetSettings](../../../api/account/SetSettings.md)

### Пример тела запроса метода [SetSettings](../../../api/account/SetSettings.md) {#request-example-body}

```json
{
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```