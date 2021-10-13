# Receive data

Receiving incoming data in the Green API is implemented via incoming webhooks. A separate incoming webhook is generated for each account event. Events can be: incoming message, receiving a previously sent message status, an incoming call, etc. For more information about account events and incoming webhooks types, refer to [Incoming webhooks types](notifications-format/type-webhook.md) section. 

Green API provides two technologies for receiving incoming webhooks:

- [Receive webhooks via HTTP API](technology-http-api.md)
- [Receive webhooks via Webhook Endpoint](technology-webhook-endpoint.md)

A detailed description of webhooks format is given in [Incoming webhooks format](notifications-format/index.md) section

To download files from incoming webhook refer to [Download files](files/DownloadFile.md) section
