# UpdateGroupName

O método altera o nome de um grupo

## Solicitação {#request}

Para alterar o nome de um grupo, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/UpdateGroupName/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros de Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`groupId` | **string** | Sim | [ID do Grupo](../chat-id.md#gus)
`groupName` | **string** | Sim | Novo Nome do Grupo

### Exemplo de uma requisição {#request-example-body}

```json
{
    "groupId": "5521999990000-1587570015@g.us",
    "groupName": "Grupo criado por Green API"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`updateGroupName` | **boolean** | Sinaliza se o nome do Grupo foi alterado com sucesso

### Exemplo de uma resposta {#response-example-body}

```json
{
    "updateGroupName": true
}
```

### Erros UpdateGroupName {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/updateGroupName/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"12345678910-1112131415@g.us\",\r\n    \"groupName\":\"Grupo criado por Green API\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```