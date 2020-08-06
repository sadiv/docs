# SetGroupAdmin

O método designa o participante de um grupo como administrador.

## Solicitação {#request}

Para colocar um contato como administrador do grupo, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SetGroupAdmin/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros de Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`groupId` | **string** | Sim | [ID do Grupo](../chat-id.md#gus)
`participantChatId` | **string** | Sim | [ID do Contato](../chat-id.md#corr) membro do grupo a ser designado como administrador

### Exemplo de uma requisição {#request-example-body}

Colocando um contato como administrador de um grupo:

```json
{
    "groupId": "5521999990000-1587570015@g.us",
    "participantChatId": "5521999990001@c.us"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`setGroupAdmin` | **boolean** | Sinaliza se o contato foi colocado como administrador do grupo com suceso

### Exemplo de uma resposta {#response-example-body}

```json
{
    "setGroupAdmin": true
}
```

### Erros SetGroupAdmin {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setGroupAdmin/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"5521999990000-1587570015@g.us\",\r\n    \"participantChatId\": \"79001234568@c.us\",\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```