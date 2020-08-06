# ClearMessagesQueue

O método foi projetado para limpar a fila de mensagens para envio.

## Solicitação {#request}

Para limpar a fila de envio, você deve utilizar a chamada da API conforme exemplo abaixo:

```
GET https://api.green-api.com/waInstance{{idInstance}}/ClearMessagesQueue/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`isCleared` | **boolean** | Sinaliza se a fila de envio foi limpa com sucesso

### Exemplo de uma resposta {#response-example-body}

```json
{
    "isCleared": true
}
```

### Erros ClearMessagesQueue {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/clearMessagesQueue/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```