# Status da Conta

Esse tipo de notificação do Webhook contém dados de status de autorização da conta.

## Webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | -----
`typeWebhook` | **string** |[Tipos de notificações de webhook](type-webhook.md). Para notificações deste tipo, o campo assume o valor `stateInstanceChanged`
`instanceData` | **object** | Informação da conta
`timestamp` | **integer** | Hora do evento no formato Timestamp UNIX
`stateInstance` | **string** | Esse parâmentro pode assumir os seguintes valores:
| | `notAuthorized` - A conta não está autorizada. Para autorizar sua conta, consulte a seção [Antes de começar](../../../before-start.md#qr)
| | `authorized` - Conta autorizada
| | `sleepMode` - A conta entrou no modo de suspensão. A condição é possível quando o telefone está desligado. Depois de ligar o telefone, pode levar até 5 minutos para converter o status da conta no valor de `autorizado`.

Campos do objeto `instanceData`

Parâmetro | Tipo | Descrição
----- | ----- | -----
`idInstance` | **integer** | ID da conta
`wid` | **string** | ID da conta do WhatsApp
`typeInstance` | **string** | Tipo de messenger para conta (padrão: whatsapp)

### Exemplo de dados vindo pelo webhook {#webhook-example-body}

```json
{
    "typeWebhook":"stateInstanceChanged",
    "instanceData": {
        "idInstance": 1,
        "wid": "5521999990000@c.us",
        "typeInstance":"whatsapp"
    },
    "timestamp": 1586700690,
    "stateInstance": "notAuthorized"
}
```
