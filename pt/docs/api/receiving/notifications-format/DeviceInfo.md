# Status do Dispositivo

Uma notificação de webhook desse tipo contém informações sobre o dispositivo e o nível da bateria em que o aplicativo [WhatsApp Business](https://www.whatsapp.com/business/) está sendo executado.

## Webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | -----
`typeWebhook` | **string** |[Tipos de notificações de webhook](type-webhook.md). Para notificações deste tipo, o campo assume o valor `deviceInfo`
`instanceData` | **object** | Informação da conta
`timestamp` | **integer** | Hora do evento no formato Timestamp UNIX
`deviceData` | **object** | Данные об устройстве

Campos do objeto `instanceData`

Parâmetro | Tipo | Descrição
----- | ----- | -----
`idInstance` | **integer** | ID da conta
`wid` | **string** | ID da conta do WhatsApp
`typeInstance` | **string** | Tipo de messenger para conta (padrão: whatsapp)

Campos do objeto `deviceData`

Parâmetro | Tipo | Descrição
----- | ----- | -----
`platform` | **string** | O sistema operacional do dispositivo que está executando o aplicativo [WhatsApp Business](https://www.whatsapp.com/business/)
`deviceManufacturer` | **string** | Fabricante do dispositivo
`deviceModel` | **string** | Modelo do dispositivo
`osVersion` | **string** | Versão do sistema operacional
`waVersion` | **string** | Versão do aplicativo [WhatsApp Business](https://www.whatsapp.com/business/) ou [WhatsApp](https://www.whatsapp.com/)
`battery` | **integer** | Nível da Bateria

### Exemplo de dados vindo pelo webhook {#webhook-example-body}

```json
{
    "typeWebhook": "deviceInfo",
    "instanceData": {
        "idInstance": 1234,
        "wid": "5521999990000@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1586700802,
    "deviceData": {
        "platform": "iphone",
        "deviceManufacturer": "Apple",
        "deviceModel": "iPhone 11",
        "osVersion": "13.4.1",
        "waVersion": "2.20.42",
        "battery": 90
    }
}
```
