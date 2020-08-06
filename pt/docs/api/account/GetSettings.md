# GetSettings

O método foi desenvolvido para obter as configurações atuais da conta.

## Solicitação {#request}

Para ter acesso as configurações de sua conta, você deve utilizar a chamada da API conforme exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetSettings/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`wid` | **string** | ID da conta do WhatsApp
`countryInstance` | **string** | Código do país da conta padrão [ISO 3166-2](https://pt.wikipedia.org/wiki/ISO_3166-2)
`typeAccount` | **string** | Tipo de conta, valores possíveis: `trial`,` production`, `vip`
`webhookUrl` | **string** | URL para receber notificações de webhook
`delaySendMessagesMilliseconds` | **integer** | [Intervalo de envio de mensagens](../send-messages-delay.md) em milissegundos. Valor mínimo 500 ms.
`markIncomingMessagesReaded` | **string** | Marcar as mensagens recebidas como lidas ou não, valores possíveis: `yes`,` no`
`proxyInstance` | **string** | Configurações de proxy da conta. Exibido dependendo das configurações de proxy. Se o proxy for privado, todos os parâmetros serão fornecidos na forma de `ip: port: login: password`. Se o proxy for o sistema, ele será fornecido dependendo das configurações do sistema proxy. Pode aceitar os valores: `ip: port: login: password` ou` system proxy`..
`outgoingWebhook` | **string** | Receba notificações do webhook sobre o status do envio / entrega / leitura de mensagens enviadas, valores possíveis: `yes`,` no`
`stateWebhook` | **string** | Receba notificações do webhook sobre alterações no status de autorização da conta, valores possíveis: `yes`,` no`
`incomingWebhook` | **string** | Receba notificações do webhook sobre mensagens e arquivos recebidos; valores possíveis: `yes`,` no`
`deviceWebhook` | **string** | Receba notificações do webhook sobre o dispositivo (telefone) e o nível da bateria, valores possíveis: `yes`,` no`

### Exemplo de uma resposta {#response-example-body}

```json
{
    "wid": "5521999990000@c.us", 
    "countryInstance": "ru",
    "typeAccount": "vip",
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "delaySendMessagesMilliseconds": 3000,
    "markIncomingMessagesReaded": "yes",
    "proxyInstance": "123.45.67.891:3435:hdhhd:i3ji3",
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```

### Erro GetSettings {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getSettings/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```