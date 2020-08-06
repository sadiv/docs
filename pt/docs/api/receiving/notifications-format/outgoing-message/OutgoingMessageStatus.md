# Status da mensagem enviada

A notificação Webhook desse tipo contém o status de uma mensagem enviada anteriormente: enviada, entregue, lida etc.

## webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | -----
`typeWebhook` | **string** | [Tipos de notificações de webhook](../type-webhook.md). Para notificações deste tipo, o campo assume o valor `outgoingMessageStatus`
`instanceData` | **object** | Informação da conta
`timestamp` | **integer** | Hora do evento no formato Timestamp UNIX
`idMessage` | **string** | Identificador da mensagem ou arquivo enviado. O identificador da mensagem enviada é retornado pelos métodos:: [SendMessage](../../../../api/sending/SendMessage.md), [SendFileByUrl](../../../../api/sending/SendFileByUrl.md), [SendFileByUpload](../../../../api/sending/SendFileByUpload.md), [SendLocation](../../../../api/sending/SendLocation.md), [SendContact](../../../../api/sending/SendContact.md), [SendLink](../../../../api/sending/SendLink.md)
`status` | **string** | O status da mensagem ou arquivo enviado. O status assume valores:
| | `sent` - Mensagem enviada
| | `delivered` - mensagem entregue ao destinatário
| | `read` - mensagem lida / visualizada / escutada pelo destinatário
| | `noAccount` - A conta do WhatsApp não está registrada no número de telefone do destinatário
| | `notInGroup` - o remetente não é um membro do chat em grupo para o qual a mensagem está sendo enviada

Campos do objeto `instanceData`

Parâmetro | Tipo | Descrição
----- | ----- | -----
`idInstance` | **integer** | ID da conta
`wid` | **string** | ID da conta do WhatsApp
`typeInstance` | **string** | Tipo de messenger para conta (padrão: whatsapp)

### Exemplo de dados vindo pelo webhook {#webhook-example-body}

```json
{
    "typeWebhook": "outgoingMessageStatus",
    "timestamp": 1586700802,
    "instanceData": {
        "idInstance": 1234,
        "wid": "5521999990000@c.us",
        "typeInstance": "whatsapp"
    },
    "idMessage": "3EB0608D6A2901063D63",
    "status": "noAccount"
}
```
