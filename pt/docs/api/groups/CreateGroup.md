# CreateGroup

O método pretende criar um bate-papo em grupo.

## Solicitação {#request}

Para criar um grupo, você deve utilizar a chamada da API conforme exemplo abaixo:

```
POST https://api.green-api.com/waInstance{{idInstance}}/CreateGroup/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros de Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`groupName` | **string** | Sim | Nome do novo bate-papo em grupo
`chatIds` | **array<string>** | Sim | Incluir [ID dos Contatos](../chat-id.md#corr) no grupo

### Exemplo de uma requisição {#request-example-body}

```json
{
    "groupName": "Group created by Green API",
    "chatIds": [
        "5521999990000@c.us",
        "5521999990001@c.us"
    ]
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Тipo |  Descrição
----- | ----- | ----- 
`created` | **boolean** | Sinaliza se o grupo foi criado
`chatId` | **string** | [ID do Grupo](../chat-id.md#gus)
`groupInviteLink` | **string** | Link para convite do Grupo

### Exemplo de uma resposta {#response-example-body}

```json
{
    "created": true,
    "chatId": "5521999990000-1587570015@g.us",
    "groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### Erros CreateGroup {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/createGroup/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupName\": \"Grupo por Green API\",\r\n    \"chatIds\": [\r\n        \"5521999990000@c.us\",\r\n        \"5521999990001@c.us\"\r\n    ]\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```