# Типы webhook уведомлений

Webhook уведомления могут быть следующих типов:

- `stateInstanceChanged` - уведомление об изменении состояния авторизации аккаунта 
- `outgoingMessageStatus` - уведомление о статусах отправки/доставки/прочтении исходящих сообщений
- `incomingMessageReceived` - уведомление о входящих сообщениях и файлах
- `deviceInfo` - уведомление об устройстве (телефоне) и уровне заряда батареи

## Получение webhook уведомлений разных типов
Для включения или отключения webhook уведомлений по типам используйте метод [SetSettings](/api/account/SetSettings)

### Пример тела запроса метода [SetSettings](/api/account/SetSettings) {#request-example-body}

```json
{
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```