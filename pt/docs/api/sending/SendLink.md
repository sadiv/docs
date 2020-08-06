# SendLink

O método foi projetado para enviar uma mensagem com um link pelo qual a visualização da imagem, o título e a descrição serão adicionados.

A imagem, o título e a descrição são obtidos da marcação [Open Graph](https://en.wikipedia.org/wiki/Facebook_Platform#Open_Graph_protocol) da página para a qual o link aponta.

A mensagem será adicionada à fila de envio. A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de envio de mensagens](../send-messages-delay.md).

## Solicitação {#request}

Para enviar um link, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendLink/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do Grupo](../chat-id.md)
`urlLink` | **string** | Sim | Endereço do link

> Recomenda-se que a página mencionada no link urlLink contenha a marcação [Open Graph](https://en.wikipedia.org/wiki/Facebook_Platform#Open_Graph_protocol). Nesse caso, a mensagem será complementada por uma figura, cabeçalho e uma breve descrição.

### Exemplo de uma requisição {#request-example-body}

Enviando um link para um contato em particular:
```json
{
    "chatId": "5521999990000@c.us",
    "urlLink": "https://green-api.com.br"
}
```

Enviando um link para um grupo:
```json
{
    "chatId": "5521999990000-1581234048@g.us",
    "urlLink": "https://green-api.com.br"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmentro | Tipo |  Descrição
----- | ----- | ----- 
`idMessage ` | **string** | ID da mensagem enviada

### Exemplo de uma resposta {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Erros SendLink {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLink/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"5521999990000@c.us\",\r\n\t\"urlLink\": \"https://green-api.com.br\"\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
