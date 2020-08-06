# GetContacts

O método visa obter a lista de contatos da conta atual.

## Solicitação {#request}

Para obter a lista de contatos da conta atual, você deve utilizar a chamada da API conforme exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetContacts/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

## Resposta {#response}


### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`id` | **string** | [ID do bate-papo do contato ou do grupo](../chat-id.md)
`name` | **string** | Nome do Contato
`type` | **string** | Tipo de Contato. Valores Possíveis:
||`user` - É um contato individual
||`group` - É um grupo


### Exemplo de uma resposta {#response-example-body}

```json
[
    {
        "id": "5521999990000@c.us",
        "name": "José da Silva",
        "type": "user"
    },
    {
        "id": "5525999990000c.us",
        "name": "Carlos Arthur",
        "type": "user"
    },
    {
        "id": "5521999990000-1479621234@g.us",
        "name": "Meu time de futebol",
        "type": "group"
    }
]
```

### Erros GetContacts {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getContacts/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```