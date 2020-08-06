# GetStateInstance

O método foi projetado para obter o status da conta.

## Solicitação {#request}

Para ter acesso ao status da sua conta, você deve utilizar a chamada da API conforme exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetStateInstance/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`stateInstance` | **string** | Pode retornar os seguintes valores:
| | `notAuthorized` - A conta não está autorizada. Para autorizar sua conta, consulte a seção [Antes de começar].(../../before-start.md#qr)
| | `authorized` - Conta Autorizada
| | `sleepMode` - A conta entrou no modo de suspensão. A condição é possível quando o telefone está desligado. Depois de ligar o telefone, pode levar até 5 minutos para converter o status da conta no valor de `autorizado`

### Exemplo de uma resposta {#response-example-body}

```json
{
    "stateInstance": "authorized"
}
```

### Erros GetStateInstance {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getStateInstance/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```