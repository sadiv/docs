# Mensagem recebida com geolocalização

Esta seção descreve os campos de webhook de notificação do objeto `messageData` específico da mensagem de geolocalização recebida.
Consulte a seção [Mensagem recebida](Webhook-IncomingMessageReceived.md) para obter uma descrição dos campos gerais das mensagens recebidas.

Para receber notificações de webhook desse tipo, duas condições devem ser atendidas:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `locationMessage`

## Webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Campos do objeto `messageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`typeMessage` | **string** | Tipo de mensagem recebida. Para mensagens deste tipo, o campo assume o valor `locationMessage`
`locationMessageData` | **object** | Objeto de dados de geolocalização recebido

Campos do objeto `locationMessageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`latitude` | **double** | Latitude da localização
`longitude` | **double** | Longitude da localização
`jpegThumbnail` | **string** | Visualizar imagem na codificação `base64`

### Exemplo de dados vindo pelo webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "552199990001@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "552199990000@c.us",
        "sender": "552199990000@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "locationMessage",
        "locationMessageData": {
            "latitude": -22.95162,
            "longitude": -43.21077,
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFx="
        }
    }
}
```
