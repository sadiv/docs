# SendContact

O método envia uma mensagem com um contato. Um cartão de visita de contato é formado e enviado para o bate-papo.
A mensagem será adicionada à fila de envio. A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de envio de mensagens](../send-messages-delay.md).

## Solicitação {#request}

Para enviar um contato, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendContact/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do Grupo](../chat-id.md)
`contact` | **object** | Sim | Objeto Contato, descrito na próxima tabela

Parâmetros do objeto de contato:

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`phoneContact ` | **integer** | Sim | número de telefone para contato em formato internacional (sem +).
`firstName` | **string** | Se `middleName`,` lastName`, `company` não forem especificados | Nome do Contato
`middleName` | **string** | Se `firstName`,` lastName`, `company` não forem especificados | Nome do Meio do Contato
`lastName` | **string** | Se `middleName`, `firstName`, `company` não forem especificados | Sobrenome do Contato
`company` | **string** | Se`middleName`, `lastName`, `firstName` não forem especificados | Nome da Empresa do Contato

### Exemplo de uma requisição {#request-example-body}

Envie uma contato para um outro contato em particular:

```json
{
    "chatId": "5521999990099@c.us",
    "contact": {
        "phoneContact": 5521999990000,
        "firstName": "Andre",
        "middleName": "Carlos",
        "lastName": "Silva",
        "company": "ACME"
    }
}
```

Enviando um contato para um grupo:

```json
{
    "chatId": "552199999009-1581234048@g.us",
    "contact": {
        "phoneContact": 5521999990000,
        "firstName": "Andre",
        "middleName": "Carlos",
        "lastName": "Silva",
        "company": "ACME"
    }
}
```

### Parâmetros de Resposta {#response-parameters}

Parâmentro | Tipo |  Descrição
----- | ----- | -----
`idMessage ` | **string** | ID da Mensagem Enviada

### Exemplo de uma resposta {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Erros SendContact {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendContact/{{apiTokenInstance}}"

payload = "{\r\n\t\"chatId\": \"5521999990000@c.us\",\r\n\t\"contact\": {\r\n\t\t\"phoneContact\": 5521999990099,\r\n    \t\"firstName\": \"André\",\r\n\t\t\"middleName\": \"Carlos\",\r\n\t\t\"lastName\": \"Silva\",\r\n\t\t\"company\": \"ACME\"\r\n\t}\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```