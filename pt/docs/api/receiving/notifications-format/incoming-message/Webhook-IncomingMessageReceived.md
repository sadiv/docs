# Caixa de Entrada

Esta seção descreve os campos gerais para mensagens de webhook recebidas do tipo `incomingMessageReceived`. Uma descrição de todos os tipos de notificações de webhook é fornecida na seção [Tipos de notificações de webhook](../type-webhook.md).

O sistema irá receber notificação de mensagens recebidas sobre os tipos a seguir:

- [Mensagem de texto recebida](TextMessage.md)
- [Mensagem de texto recebida com URL](ExtendedTextMessage.md)
- [Mensagem recebida com imagem, vídeo, áudio, documento](ImageMessage.md)
- [Mensagem recebida com geolocalização](LocationMessage.md)
- [Mensagem recebida com contato](ContactMessage.md)

## Webhook para o objeto `incomingMessageReceived` {# webhook-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | -----
`typeWebhook` | **string** | [Tipos de notificações de webhook](../type-webhook.md). Para uma notificação de webhook desse tipo, o campo assume o valor de `incomingMessageReceived`
`instanceData` | **object** | Informação da conta
`timestamp` | **integer** | Hora do evento no formato Timestamp UNIX
`idMessage` | **string** | ID da mensagem recebida
`senderData` | **object** | Detalhes do remetente da mensagem ou arquivo
`messageData` | **object** | Detalhes da mensagem ou arquivo recebidos

Campos do objeto instanceData

Parâmetro | Tipo | Descrição
----- | ----- | -----
`idInstance` | **integer** | ID da conta
`wid` | **string** | ID da conta do WhatsApp
`typeInstance` | **string** | Tipo de messenger para conta (nesse caso sempre será whatsapp)

Campos do objeto senderData

Parâmetro | Tipo | Descrição
----- | ----- | -----
`chatId` | **string** | [ID do Grupo](../../../chat-id.md), em que a mensagem ou arquivo é recebido
`sender` | **string** | [ID do Remetente](../../../chat-id.md#corr) remetente da mensagem ou arquivo
`senderName` | **string** | Nome do Remetente

### Campos do objeto messageData

O objeto messageData possui campos diferentes, dependendo do tipo de mensagem recebida:

- [Mensagem de texto recebida](TextMessage.md)
- [Mensagem de texto recebida com URL](ExtendedTextMessage.md)
- [Mensagem recebida com imagem, vídeo, áudio, documento](ImageMessage.md)
- [Mensagem recebida com geolocalização](LocationMessage.md)
- [Mensagem recebida com contato](ContactMessage.md)

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
       // Dependendo de typeMessage = textMessage || imageMessage || videoMessage || documentMessage || audioMessage || locationMessage || contactMessage || extendedTextMessage
       ...
       ...
       ...
        }
    }
}
```