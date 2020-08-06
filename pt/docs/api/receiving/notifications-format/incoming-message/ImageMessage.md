# Mensagem recebida com imagem, vídeo, áudio, documento

Esta seção descreve os campos de notificação da web do objeto `messageData` específico de uma mensagem recebida com uma imagem, vídeo, áudio ou documento. Consulte a seção [Mensagem recebida](Webhook-IncomingMessageReceived.md) para obter uma descrição dos campos gerais das mensagens recebidas.

Para receber notificações de webhook desse tipo, duas condições devem ser atendidas:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `imageMessage` || `videoMessage` || `documentMessage` || `audioMessage`

## Webhook {#webhook}

### Parâmetros do Webhook {#webhook-parameters}

Campos do objeto `messageData`

Parâmetro | Тipo | Descrição
----- | ----- | -----
`typeMessage` | **string** | Tipo de mensagem recebida. Para mensagens deste tipo, o campo assume o valor: `imageMessage`,` videoMessage`, `documentMessage`,` audioMessage`
`fileMessageData ` | **object** | Objeto de dados do arquivo recebido

Campos do objeto `fileMessageData` 

Parâmetro | Тipo | Descrição
----- | ----- | -----
`downloadUrl` | **string** | Link para baixar o arquivo
`caption` | **string** | Descrição do arquivo

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
        "typeMessage":"imageMessage",
        "fileMessageData":{
            "downloadUrl":"https://api.green-api.com/waInstance1234/downloadFile/19136A974392FA8CF584D70DD0E1AEDF",
            "caption":"Cenário"
        }
    }
}
```
