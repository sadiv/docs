# AddGroupParticipant

O método adiciona o participante ao bate-papo em grupo.

## Solicitação {#request}

Para adicionar um contato um grupo, você deve utilizar a chamada da API conforme exemplo abaixo:

```
POST https://api.green-api.com/waInstance{{idInstance}}/AddGroupParticipant/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parêmtros da Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`groupId` | **string** | Sim | [ID do Grupo](../chat-id.md#gus)
`participantChatId` | **string** | Sim | [ID do Grupo](../chat-id.md#corr) a ser adicionado ao bate-papo em grupo.


### Exemplo de uma requisição {#request-example-body}

Adicionar contato ao grupo:

```json
{
    "groupId": "5521999990000-1587570015@g.us",
    "participantChatId": "5521999990001@c.us"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Тipo |  Descrição
----- | ----- | ----- 
`addParticipant` | **boolean** | Sinaliza se o contato foi adicionado com sucesso ao grupo.

### Exemplo de uma resposta {#response-example-body}

```json
{
    "addParticipant": true
}
```

### Erros AddGroupParticipant {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/addGroupParticipant/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"5521999990000-1581234048@g.us\",\r\n\t\"participantChatId\": \"79001234568@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```