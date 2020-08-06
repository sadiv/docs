# Tipos de notificações de webhook

As notificações do Webhook podem ser dos seguintes tipos:

- `stateInstanceChanged` - notificação sobre a alteração do status de autorização da conta
- `outgoingMessageStatus` - notificação do status de envio / entrega / leitura de mensagens enviadas
- `incomingMessageReceived` - notificação de mensagens e arquivos recebidos
- `deviceInfo` - notificação sobre o dispositivo (telefone) e o nível da bateria

## Recebendo notificações de webhook de vários tipos
Para ativar ou desativar as notificações do webhook por tipo, use o método [SetSettings](../../../api/account/SetSettings.md)

### Corpo da requisição de exemplo [SetSettings](../../../api/account/SetSettings.md) {#request-example-body}

```json
{
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```