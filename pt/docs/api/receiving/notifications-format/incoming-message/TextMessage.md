# Mensagem de texto recebida

Esta seção descreve os campos de notificação da web do objeto `messageData` específico da mensagem de texto recebida. Consulte a seção [Mensagem recebida](Webhook-IncomingMessageReceived.md) para obter uma descrição dos campos gerais das mensagens recebidas.
Para receber notificações de webhook desse tipo, duas condições devem ser atendidas:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `textMessage`

## Webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Campos do objeto `messageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`typeMessage` | **string** | Tipo de mensagem recebida. Para mensagens deste tipo, o campo assume o valor `textMessage`
`textMessageData` | **object** | Objeto de dados da mensagem de texto

Campos do objeto `textMessageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`textMessage` | **string** | Mensagem de texto

### Exemplo de dados vindo pelo webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "5521999990001@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "5521999990000@c.us",
        "sender": "5521999990000@c.us",
        "senderName": "Green API"
    },
    "messageData":{
        "typeMessage":"textMessage",
        "textMessageData":{
            "textMessage":"Eu uso Green-API para enviar mensagens para você!"
        }
    }
}
```
