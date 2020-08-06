# GetAvatar

O método retorna a imagem de perfil do contato ou do grupo.

## Solicitação {#request}

Para retorna a imagem de um perfil, você deve realizar uma requisição utilizando o método abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/GetAvatar/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte [Antes de Começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório| Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do bate-papo do contato ou do grupo](../chat-id.md)

### Exemplo da Requisição {#request-example-body}

Para obter a imagem de Peril:

```json
{
    "chatId": "5521999990000@c.us"
}
```

Para obter a imagem de Perfil de um Grupo:

```json
{
    "chatId": "5521999990000-1581234048@g.us"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmentro | Tipo |  Descrição
----- | ----- | ----- 
`existsWhatsapp` | **boolean** | Sinalizador de presença da conta do WhatsApp no ​​número de telefone do correspondente
`urlAvatar` | **string** | Link para o perfil de um contato ou bate-papo em grupo. O parâmetro assume um valor vazio se a imagem de perfil não estiver instalado ou o contato não tiver uma conta do WhatsApp (`existeWhatsapp` =` false`)
`reason` | **string** | A razão pela qual a imagem de perfil não foi verificada. Situação quando a verificação falhou, os valores possíveis são:
| | `bad request data` - Formato de número de telefone inválido. Ou código de bate-papo
| | `get avatar timeout limit exceeded` - Limite de tempo resposta para obtenção da imagem do perfil foi excedido.

### Exemplo de uma resposta {#response-example-body}

```json
{
  	"existsWhatsapp": true,
 	  "urlAvatar": "https://pps.whatsapp.net/v/link/to/the/image"
}
```

### Erros GetAvatar {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md) [Стандартные ошибки](../common-errors.md)

Código HTTP | ID do Erro | Descrição
----- | ----- | -----
400|`bad request data`| Formato de número de telefone inválido. Ou código de bate-papo
400|`get avatar timeout limit exceeded`| Limite de tempo resposta para obtenção da imagem do perfil foi excedido.

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getAvatar/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"79001234567@c.us\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```