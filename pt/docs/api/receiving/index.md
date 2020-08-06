# Obtendo dados

O recebimento de dados recebidos na Green API é realizado através de notificações recebidas. Uma notificação de entrada separada é gerada para cada evento da conta. Os seguintes eventos podem atuar como: receber uma mensagem de entrada, receber o status de uma mensagem enviada anteriormente etc. Para obter mais informações sobre eventos da conta e tipos de notificação de entrada, consulte [Tipos de notificação de entrada](notifications-format/type-webhook.md).

Existem duas tecnologias na API verde para receber notificações recebidas:

- [Receba notificações via API HTTP (recomendado)](technology-http-api.md)
- [Receba notificações via Webhook Endpoint](technology-webhook-endpoint.md)

O formato de notificação é descrito em detalhes na seção [Formato de notificação de entrada](notifications-format/index.md)

Para baixar arquivos de notificações recebidas, consulte a seção [Recebendo arquivos](files/DownloadFile.md)