# Mensagem de texto recebida com URL

Esta seção descreve os campos de notificação da web do objeto `messageData` específico para uma mensagem de texto recebida com uma URL. Consulte a seção [Mensagem recebida](Webhook-IncomingMessageReceived.md) para obter uma descrição dos campos gerais das mensagens recebidas.

Para receber notificações de webhook desse tipo, duas condições devem ser atendidas:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `extendedTextMessage`

## Webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Campos do objeto `messageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`typeMessage` | **string** | Tipo de mensagem recebida. Para mensagens deste tipo, o campo assume o valor `extendedTextMessage`
`extendedTextMessageData` | **object** | Objeto de dados do link recebido com metadados

Campos do objeto `extendedTextMessageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`text` | **string** | Texto do link
`description` | **string** | Descrição do Link
`title` | **string** | Título do link
`previewType` | **string** | Tipo de visualização do link
`jpegThumbnail` | **string** | Visualizar imagem na codificação `base64`

### Exemplo de dados vindo pelo webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "55999990001@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "55999990000@c.us",
        "sender": "55999990000@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "extendedTextMessage",
        "extendedTextMessageData": {
            "text": "https://green-api.com.br/docs/video",
            "description": "A documentação da Green API mostra como você pode desenvolver um WhatsApp Bot",
            "title": "Como desenvolver um WhatsApp Bot",
            "previewType": "video",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFxQYG=="
        }
    }
}
```
