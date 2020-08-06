# Receber notificações via endpoint do Webhook

A tecnologia Webhook permite que você receba notificações diretamente no seu servidor. Isso significa que o servidor da Green API chamará o método publicado no seu lado, no seu servidor. As vantagens dessa tecnologia são o recebimento mais rápido de notificações, limitadas apenas pela velocidade de processamento de notificações no seu servidor. As desvantagens incluem a complexidade da implementação e configuração, bem como a possível perda de notificações quando o servidor não está disponível.

> As notificações recebidas podem ser perdidas quando o servidor não está disponível. Se o servidor não estiver disponível ou não puder processar uma notificação recebida, não haverá tentativas repetidas de entrega para essa notificação. Esse aviso será perdido. Portanto, configure seu servidor para que ele esteja sempre disponível para processar notificações recebidas ou use a tecnologia [Recebendo notificações via API HTTP](technology-http-api.md), na qual a entrega de entrada é fornecida por 24 notificações de entrada.

## Configuração do Servidor

Você precisará concluir as seguintes etapas para receber notificações usando a tecnologia Webhook:

- publicar um endereço IP na Internet
- implementar a lógica do processamento de notificações recebidas no endereço IP especificado

### Endereço IP público

Para receber notificações, você precisa de um endereço IP público, que estará aberto e disponível na Internet. Dessa forma, o servidor da Green API poderá fazer uma chamada para o servidor no endereço especificado e enviar uma notificação de entrada.

### Processamento de notificações recebidas

Depois de receber uma chamada para o endereço IP do seu servidor, você precisará processar a notificação recebida. Um exemplo do código de processamento de notificações recebidas no [NodeJS](https://nodejs.org) pode ser exibido no [arquivo](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveWebhook.js)

## Configurações da conta {#webhookUrl}

Você precisa configurar sua conta antes de receber notificações. A conta pode ser configurada no seu código de programação (#SetSettings) usando o método [SetSettings](../account/SetSettings.md).

### Método de configuração [SetSettings](../account/SetSettings.md) {#SetSettings}

Para configurar o recebimento de notificações recebidas usando a tecnologia Webhook, você precisa especificar o valor do seu endereço IP ou do seu nome de domínio como o parâmetro `webhookUrl`. Por exemplo:

```
https://84.211.100.201:3000/green-api/webhook/
```

Você também precisa especificar quais tipos de notificação você precisa receber. Para incluir notificações recebidas por tipo, bem como especificar o parâmetro `webhookUrl`, use o método [SetSettings](../account/SetSettings.md).

#### Exemplo de método de solicitação [SetSettings](../account/SetSettings.md)

```json
{
    "webhookUrl": "https://84.211.100.201:3000/green-api/webhook/",
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```

## Receba notificações recebidas

Depois de concluir as configurações da conta, você pode começar a receber notificações. Um exemplo do código de processamento de notificações recebidas em [NodeJS](https://nodejs.org) pode ser visualizado no [arquivo](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveWebhook.js).

## Depurando notificações recebidas

Você pode usar qualquer serviço gratuito na Internet, como o serviço [Webhook.Site](https://webhook.site/), para depurar as notificações recebidas. O serviço emite um endereço exclusivo (URL) necessário para [configurar](#webhookUrl) como o valor do parâmetro `webhookUrl`.

Uma descrição detalhada do formato das notificações recebidas é fornecida na seção [Formato das notificações recebidas](notifications-format/index.md).