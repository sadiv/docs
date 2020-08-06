# LeaveGroup

O método desconecta o usuário da conta atual de um grupo.

## Solicitação {#request}

Para sair de um grupo, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/LeaveGroup/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros de Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`groupId` | **string** | Sim | [ID do Grupo](../chat-id.md#gus), de onde deseja sair.

### Exemplo de uma requisição {#request-example-body}

```json
{
    "groupId": "5521999990000-1587570015@g.us"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`leaveGroup` | **boolean** | Флаг выхода из группы

### Exemplo de uma resposta {#response-example-body}

```json
{
    "leaveGroup": true
}
```

### Erros LeaveGroup {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/leaveGroup/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"5521999990000-1587570015@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```