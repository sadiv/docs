# Logout

O método foi projetado para efetuar o logout de sua conta.

## Solicitação {#request}

Para efetuar o logout da sua conta, você deve utilizar a chamada da API conforme exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/Logout/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`isLogout` | **boolean** | Resultado de logout da conta do WhatsApp

### Exemplo de uma resposta {#response-example-body}

```json
{
    "isLogout": true
}
```

### Erros Logout {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/logout/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```