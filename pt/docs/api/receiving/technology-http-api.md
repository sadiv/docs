# Receba notificações via API HTTP (recomendado)

Você pode receber notificações recebidas (mensagens, status) por meio de solicitações da API HTTP, à medida que outros métodos da Green API são implementados. Isso garante a ordem cronológica na qual as notificações são ordenadas, na ordem em que foram recebidas seguindo uma fila [FIFO](https://pt.wikipedia.org/wiki/FIFO). A tecnologia da API HTTP é uma maneira recomendada de receber notificações recebidas. É mais fácil obter dados sobre essa tecnologia em comparação com o [Webhook Endpoint](technology-webhook-endpoint.md). Uma vantagem adicional é a entrega garantida de notificações recebidas. Todas as notificações recebidas são armazenadas na fila e aguardam por até 24 horas.

Para receber notificações recebidas, é necessário chamar dois métodos [ReceiveNotification](technology-http-api/ReceiveNotification.md) e [DeleteNotification](technology-http-api/DeleteNotification.md). O método [ReceiveNotification](technology-http-api/ReceiveNotification.md) recupera uma notificação recebida. O método [DeleteNotification](technology-http-api/DeleteNotification.md) confirma o recebimento e o processamento bem-sucedidos da notificação. Para obter detalhes sobre os métodos, consulte as seções relevantes [ReceiveNotification](technology-http-api/ReceiveNotification.md) e [DeleteNotification](technology-http-api/DeleteNotification.md).

> O período de armazenamento das notificações recebidas é de 24 horas.

## Configurações da conta

Você precisa configurar sua conta antes de receber notificações. A conta pode ser configurada [programaticamente](#SetSettings) usando o método [SetSettings](../account/SetSettings.md)

### Método de Configuração [SetSettings](../account/SetSettings.md) {#SetSettings}

Para configurar o recebimento de notificações de entrada usando a tecnologia HTTP API, é necessário especificar o valor `webhookUrl` como o parâmetro:

```
https://webhook.green-api.com/
```

Você também precisa especificar quais tipos de notificação você precisa receber. Para incluir notificações recebidas por tipo, bem como especificar o parâmetro `webhookUrl`, use o método [SetSettings](../account/SetSettings.md).

#### Exemplo de método de solicitação [SetSettings](../account/SetSettings.md)

```json
{
    "webhookUrl": "https://webhook.green-api.com/",
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```

## Receber Notificações Recebidas

Depois de concluir as configurações da conta, você pode continuar recebendo notificações pelos métodos [ReceiveNotification](technology-http-api/ReceiveNotification.md) e [DeleteNotification](technology-http-api/DeleteNotification.md). Exemplo de recebimento de código de notificação em [NodeJS] [NodeJS](https://nodejs.org) pode ser visualizado no arquivo [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js).

Uma descrição detalhada do formato das notificações recebidas é apresentada na seção [Formato de notificação de entrada](notifications-format/index.md).