# CheckWhatsapp

O método verifica a presença de uma conta do WhatsApp no ​​número de telefone.

## Solicitação {#request}

Para verificar se o número em questão possui uma conta WhatsApp, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/CheckWhatsapp/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`phoneNumber` | **integer** | Sim | Número de telefone do destinatário em formato internacional: Exemplo: `5521999990000`

### Exemplo da Requisição {#request-example-body}

```json
{
    "phoneNumber": 5521999990000
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmentro | Tipo |  Descrição
----- | ----- | ----- 
`existsWhatsapp` | **boolean** | Existem uma conta no WhatsApp no ​​número deste telefone

### Exemplo de uma resposta {#response-example-body}

```json
{
    "existsWhatsapp": true
}
```

### Erros CheckWhatsapp {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

Código HTTP | ID do Erro | Descrição
----- | ----- | -----
400 | `bad phone number, valid 11 or 12 digits` | Formato de número de telefone inválido.
400 | `check phone number timeout limit exceeded` | A resposta da verificação do número de telefone expirou

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/checkWhatsapp/{{apiTokenInstance}}"

payload = "{\r\n    \"phoneNumber\": 5521999990000\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```