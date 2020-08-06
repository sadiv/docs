# GetGroupData

O método obtém dados de um grupo.

## Solicitação {#request}

Para ter acesso aos dados de um grupo, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetGroupData/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros de Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`groupId` | **string** | Sim | [ID do Grupo](../chat-id.md#gus)

### Exemplo de uma requisição {#request-example-body}

```json
{
    "groupId": "5521999990000-1587570015@g.us"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`groupId` | **string** | [ID do Grupo](../chat-id.md#gus)
`owner` | **string** | [ID do contato](../chat-id.md#corr) proprietário do grupp
`subject` | **string** | Nome do Grupo
`creation` | **integer** | Hora de criação do grupo no formato Unix
`participants` | **array** | Objeto contendo lista de membros do grupo
`subjectTime` | **integer** |Hora de criação do nome do grupo no formato Unix
`subjectOwner` | **string** | [ID do Grupo](../chat-id.md#corr) que criou o grupo
`groupInviteLink` | **string** | Link para convite de grupo

Objetos que constam no campo `participants`

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`id` | **string** | [ID do Grupo](../chat-id.md#corr) membro do grupo
`isAdmin` | **boolean** | Sinaliza se o usuário é um administrador do grupo
`isSuperAdmin` | **boolean** | Sinaliza se o usuário é o superadministrador do grupo

### Exemplo de uma resposta {#response-example-body}

```json
{
	"groupId": "5521999990000-1587570015@g.us",
	"owner": "5521999990000@c.us",
	"subject": "Grupo Green API",
	"creation": 1587570015,
	"participants": [
		{
			"id": "5521999990000@c.us",
			"isAdmin": true,
			"isSuperAdmin": true
		},
		{
			"id": "5521999990001@c.us",
			"isAdmin": true,
			"isSuperAdmin": false
		},
		{
			"id": "5521999990002@c.us",
			"isAdmin": false,
			"isSuperAdmin": false
		}
	],
	"subjectTime": 1587737715,
	"subjectOwner": "5521999990000@c.us",
	"groupInviteLink": "https://chat.whatsapp.com/xxxxxxxxxxxxxxxxxxxxxx"
}
```

### Erros GetGroupData {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getGroupData/{{apiTokenInstance}}"

payload = "{\r\n\t\"groupId\": \"5521999990000-1587570015@g.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```