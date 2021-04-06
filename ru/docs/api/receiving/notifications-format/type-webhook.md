# Типы входящих уведомлений

Входящие уведомления могут быть следующих типов:

- [incomingMessageReceived](incoming-message/Webhook-IncomingMessageReceived.md) - уведомление о входящих сообщениях и файлах
- [outgoingMessageReceived](outgoing-message/OutgoingMessage.md) - уведомление о сообщении, отправленного с телефона
- [outgoingMessageStatus](outgoing-message/OutgoingMessageStatus.md) - уведомление о статусах отправки/доставки/прочтении исходящих сообщений
- [stateInstanceChanged](StateInstanceChanged.md) - уведомление об изменении состояния авторизации аккаунта
- [deviceInfo](DeviceInfo.md) - уведомление об устройстве (телефоне) и уровне заряда батареи
- [incomingCall](IncomingCall.md) - уведомление о входящем звонке

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