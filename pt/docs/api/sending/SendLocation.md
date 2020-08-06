# SendLocation


O método foi projetado para enviar uma mensagem de geolocalização.

A mensagem será adicionada à fila de envio. A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de envio de mensagens](../send-messages-delay.md).

## Solicitação {#request}

Para enviar um geo-localização, você deve utilizar a chamada da API conforme exemplo abaixo:

```
POST https://api.green-api.com/waInstance{{idInstance}}/SendLocation/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do Grupo](../chat-id.md)
`nameLocation` | **string** | Não | Nome do Local
`address` | **string** | Não | Endereço do Local
`latitude` | **double** | Sim | Latitude
`longitude` | **double** | Sim | Longitude

### Exemplo de uma requisição {#request-example-body}

Enviando um geo-localização para um contato em particular:
```json
{
    "chatId": "5521999990000@c.us",
    "nameLocation": "Cristo Redentor",
    "address": "Parque Nacional da Tijuca - Alto da Boa Vista, Rio de Janeiro - RJ",
    "latitude": -22.95162,
    "longitude": -43.21077
}
```

Enviando um geo-localização para um grupo:
```json
{
    "chatId": "5521999990000@-1581234048@g.us",
    "nameLocation": "Cristo Redentor",
    "address": "Parque Nacional da Tijuca - Alto da Boa Vista, Rio de Janeiro - RJ",
    "latitude": -22.95162,
    "longitude": -43.21077
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

### Erros SendLocation {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendLocation/{{apiTokenInstance}}"

payload = "{\r\n    \"chatId\": \"5521999990000@c.us\",\r\n    \"nameLocation\": \"Cristo Redentor\",\r\n    \"address\": \"Parque Nacional da Tijuca - Alto da Boa Vista, Rio de Janeiro - RJ\",\r\n   \t\"latitude\": -22.95162,\r\n    \"longitude\": -43.21077\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```