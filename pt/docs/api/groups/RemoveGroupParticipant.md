# RemoveGroupParticipant

O método remove o contato participante de um grupo.

## Solicitação {#request}

Para remover o contato de um grupo, você deve utilizar a chamada da API conforme exemplo abaixo:

```
POST https://api.green-api.com/waInstance{{idInstance}}/RemoveGroupParticipant/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros de Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`groupId` | **string** | Sim | [ID do Grupo](../chat-id.md#gus)
`participantChatId` | **string** | Sim | [ID do Contato](../chat-id.md#corr) membro a ser removido do grupo

### Exemplo de uma requisição {#request-example-body}

Removendo um contato de um grupo:

```json
{
    "groupId": "5521999990000-1587570015@g.us",
    "participantChatId": "79001234565@c.us"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`removeParticipant` | **boolean** | Sinaliza se o contato foi removido com sucesso do grupo

### Exemplo de uma resposta {#response-example-body}

```json
{
    "removeParticipant": true
}
```

### Erros RemoveGroupParticipant {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/removeGroupParticipant/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"5521999990000-1587570015@g.us\",\r\n    \"participantChatId\": \"79001234568@c.us\",\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```