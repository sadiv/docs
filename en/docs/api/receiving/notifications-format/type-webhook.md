# Incoming webhooks types

Incoming webhooks may be of the below types:

- [incomingMessageReceived](incoming-message/Webhook-IncomingMessageReceived.md) - incoming messages and files notification
- [outgoingMessageReceived](outgoing-message/OutgoingMessage.md) - notification about a message sent from phone
- [outgoingMessageStatus](outgoing-message/OutgoingMessageStatus.md) - notification about outgoing messages sending/delivering/reading statuses
- [stateInstanceChanged](StateInstanceChanged.md) - account authorization state change notification 
- [statusInstanceChanged](StatusInstanceChanged.md) - account socket state change notification
- [deviceInfo](DeviceInfo.md) - device (phone) and battery level notification 
- [incomingCall](IncomingCall.md) - incoming call notification 

## Get webhooks of different types
To enable or disable webhooks by types, use [SetSettings](../../../api/account/SetSettings.md) method

### Method request body example [SetSettings](../../../api/account/SetSettings.md) {#request-example-body}

```json
{
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
    "statusInstanceChangedWebhook": "yes"
}
```
