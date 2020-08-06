# ShowMessagesQueue

O método exibe uma lista de mensagens na fila para envio. A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de Mensagens](../send-messages-delay.md).

## Solicitação {#request}

Para exibir as mensagens na fila de envio, você deve utilizar a chamada da API conforme exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/ShowMessagesQueue/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Campos Retornados:

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`typeMessage` | **string** | Tipo de mensagem, valores possíveis:
| | `textMessage` - mensagem de texto
| | `imageMessage` - mensagem com imagem
| | `videoMessage` - mensagem com vídeo
| | `documentMessage` - mensagem com arquivo de documento
| | `audioMessage` - mensagem de áudio
| | `locationMessage` - messagem de geo-localização
| | `contactMessage` - mensagem de um contato anexado
| | `extendedTextMessage` - mensagem com link de visualização
`chatId` | **string** | [ID do Contato](../chat-id.md) para qual mensagem será enviada
`message` | **string** |  texto da mensagem se `typeMessage` =` textMessage` / `locationMessage` /` contactMessage` / `extendedTextMessage`
`fileName` | **string** | O nome do arquivo a ser enviado se `typeMessage` =` imageMessage` / `videoMessage` /` documentMessage` / `audioMessage`

### Exemplo de uma resposta {#response-example-body}

```json
[
    {
        "typeMessage": "textMessage",
        "chatId": "5521999990001@c.us",
        "message": "Eu uso Green API para enviar essa mensagem para você"
    },
    {
        "typeMessage": "imageMessage",
        "chatId": "5521999990002@c.us",
        "fileName": "image.jpg"
    }
]
```

### Erros ShowMessagesQueue {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/showMessagesQueue/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```