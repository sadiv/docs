# Reboot

O método foi projetado para reiniciar a conta.

## Solicitação {#request}

Para reiniciar sua conta, você deve utilizar a chamada da API conforme exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/Reboot/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`isReboot` | **boolean** | Resultado de reinicialização da conta do WhatsApp

### Exemplo de uma resposta {#response-example-body}

```json
{
    "isReboot": true
}
```

### Erros Reboot {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/reboot/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```