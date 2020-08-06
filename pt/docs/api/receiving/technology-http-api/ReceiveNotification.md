# ReceiveNotification

O método para receber uma notificação de entrada da fila de notificações.

> O método ReceiveNotification aguarda o recebimento de uma notificação dentro de 20 segundos. A chamada do método termina com uma resposta vazia, caso o tempo limite seja atingido. Se uma notificação aparecer na fila dentro de 20 segundos, a chamada do método será interrompida e o método retornará a notificação recebida. 

Depois de receber e processar a notificação recebida, você precisa excluir a notificação da fila. Isso requer o método [DeleteNotification](DeleteNotification.md). Depois de chamar o método [DeleteNotification](DeleteNotification.md), a notificação será considerada aceita e processada e será excluída permanentemente da fila. Dessa forma, a próxima chamada para o método [ReceiveNotification](#request) retornará a próxima notificação da fila na ordem de recebimento das notificações na fila.

> O período de armazenamento de notificações recebidas na fila é de 24 horas.

> Notificações sao recebidas de fora da fila na ordem [FIFO](https://pt.wikipedia.org/wiki/FIFO)

## Requisição {#request}

Para receber a próxima notificação de entrada da fila, é necessário fazer uma requisição como no exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/ReceiveNotification/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../../before-start.md#parameters).


## Resposta {#response}

### Parâmetros de Consulta {#request-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | -----
`receiptId ` | **integer** | ID da Notificacão para ser utilizado na exclusão pelo método [DeleteNotification](DeleteNotification.md)
`body ` | **object** | Notificação recebida conforme [Formato de notificação de entrada](../notifications-format/index.md)  

### Exemplo de resposta {#response-example-body}

```json
{
    "receiptId": 1234567,
    "body": {
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
        "messageData":{
            "typeMessage":"textMessage",
            "textMessageData":{
                "textMessage":"I use Green-API to send this message to you!"
            }
        }
    }
}
```

### Erros ReceiveNotification {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../../common-errors.md)

Código HTTP | Identificador de erro | Descrição
----- | ----- | -----
400 | `Parameter idInstance not an integer` | O parâmetro `idInstance` não está especificado ou contém caracteres não numéricos
400 | `Parameter apiTokenInstance not define` | Nenhum parâmetro `apiTokenInstance` especificado

## Código Exemplo em Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/ReceiveNotification/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

Exemplo de código de notificação em [NodeJS](https://nodejs.org) pode ser visualizado no arquivo [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js)