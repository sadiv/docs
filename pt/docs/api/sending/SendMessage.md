# SendMessage

O método é destinado ao envio de uma mensagem de texto para um contato particular ou em grupo.
A mensagem será adicionada à fila de envio. A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de envio de mensagens](../send-messages-delay.md).

## Solicitação {#request}

Para enviar uma mensagem, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendMessage/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do Grupo](../chat-id.md)
message ` | **string** | Sim | Mensagem de texto. Caracteres Emoji sào suportados 😃 

> O comprimento máximo de uma mensagem de texto é 4096 caracteres.

### Exemplo de uma requisição {#request-example-body}

Enviando uma mensagem para um contato em particular:
```json
{
    "chatId": "5521999990001@c.us",
    "message": "Estou usando Green-API para mandar essa mensagem para você"
}
```

Enviando uma mensagem para um grupo:
```json
{
    "chatId": "5521999990001-1581234048@g.us",
    "message": "Estou usando Green-API para mandar essa mensagem para você"
}
```
## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmentro | Tipo |  Descrição
----- | ----- | ----- 
`idMessage ` | **string** | ID da mensagem enviada

### Exemplo de uma resposta {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Erros SendMessage {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendMessage/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"5521999990001@c.us\",\r\n\t\"message\": \"Estou usando Green-API para mandar essa mensagem para você\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```