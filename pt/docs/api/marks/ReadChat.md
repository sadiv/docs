# ReadChat

O método foi projetado para marcar as mensagens de bate-papo como lidas. Todas as mensagens de bate-papo podem ser marcadas como lidas ou apenas uma mensagem especificada.

## Solicitação {#request}

Para marcar mensagens lidas, você deve utilizar a chamada da API conforme exemplo abaixo:

```
POST https://api.green-api.com/waInstance{{idInstance}}/ReadChat/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros de Solicitação {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do Contato](../chat-id.md)
`idMessage` | **string** | Não | [ID do Contato] da mensagem recebida, que deve ser marcada como lida. Se não especificado, todas as mensagens de chat não lidas serão marcadas como lidas..

### Exemplo de uma requisição {#request-example-body}

Marca de leitura de uma mensagem de um contato:

```json
{
    "chatId": "55219999900000@c.us",
    "idMessage": "B275A7AA0D6EF89BB9245169BDF174E6"
}
```

Marca de leitura de todas as mensagens com um determinado contato:

```json
{
    "chatId": "55219999900000@c.us"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`setRead` | **boolean** | Sinaliza se a mensagem foi marcada como lida com sucesso

### Exemplo de uma resposta {#response-example-body}

```json
{
    "setRead": true
}
```

### Erros ReadChatMessage {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/readChat/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"55219999900000@c.us\",\r\n\t\"idMessage\": \"B275A7AA0D6EF89BB9245169BDF174E6\"\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```