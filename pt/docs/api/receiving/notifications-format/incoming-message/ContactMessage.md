# Mensagem recebida com Contato

Esta seção descreve os campos de notificação da web do objeto `messageData` específico para uma mensagem recebida com um contato. Consulte a seção [Mensagem recebida](Webhook-IncomingMessageReceived.md) para obter uma descrição dos campos gerais das mensagens recebidas.

Para receber notificações de webhook desse tipo, duas condições devem ser atendidas:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `contactMessage`


## Webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Campos do objeto `messageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`typeMessage` | **string** | Tipo de mensagem recebida. Para mensagens deste tipo, o campo assume o valor `contactMessage`
`contactMessageData` | **object** | Objeto de dados de contato recebido.

Campos do objeto `contactMessageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`displayName` | **string** | Nome de exibição do contato
`vcard` | **string** | Estrutura do VCard (cartão de visita de contato)

### Exemplo de dados vindo pelo webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "5521999990000@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "5521999990001@c.us",
        "sender": "5521999990001@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "contactMessage",
        "contactMessageData": {
            "displayName": "Carlos André Silva",
            "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Silva;Winner;;;\nFN:Carlos André Sima\nORG:Image\nTITLE:\nitem1.TEL;waid=5521999990000:+55 (21) 99999-0000\nitem1.X-ABLabel:Celular\nEND:VCARD"
        }
    }
}
```
