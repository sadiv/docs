# SetSettings

O método é destinado a definir configurações da conta.

> Quando esse método é chamado, a conta é reiniciada.

## Solicitação {#request}

Para definir as configurações da sua conta, você deve utilizar a chamada da API conforme exemplo abaixo::
```
POST https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

É permitido especificar parâmetros seletivamente. Pelo menos um parâmetro deve ser especificado.

Parâmetro | Тipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`countryInstance` | **string** | Não | Código do país da conta padrão [ISO 3166-2](https://pt.wikipedia.org/wiki/ISO_3166-2)
`webhookUrl` | **string** | Não | URL para o envio de notificações de webhook. Se você deseja desativar o recebimento de notificações de webhook, deixe como vazio
`delaySendMessagesMilliseconds` | **integer** | Não | [Intervalo de envio de mensagens](../send-messages-delay.md) em milissegundos. Valor mínimo 500 ms.
`markIncomingMessagesReaded` | **string** | Não | Marque as mensagens recebidas como lidas. Valores possíveis: `sim`,` não`
`proxyInstance` | **string** | Não | Proxies para a conta no formato `{ip}: {port}: {login}: {password}`, se você deseja que a conta funcione no seu proxy, os proxies do sistema são usados ​​por padrão.
`outgoingWebhook` | **string** | Não | Receba notificações do webhook sobre o status do envio / entrega / leitura de mensagens enviadas, valores possíveis: `yes`,` no`
`stateWebhook` | **string** | Não | Receba notificações do webhook sobre alterações no status de autorização da conta, valores possíveis: `yes`,` no`
`incomingWebhook` | **string** | Não | Receba notificações do webhook sobre mensagens e arquivos recebidos; valores possíveis: `yes`,` no`
`deviceWebhook` | **string** | Não | Receba notificações do webhook sobre o dispositivo (telefone) e o nível da bateria, valores possíveis: `yes`,` no`

### Exemplo de uma requisição {#request-example-body}

```json
{
    "countryInstance": "br",
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "delaySendMessagesMilliseconds": 1000,
    "markIncomingMessagesReaded": "no",
    "proxyInstance": "100.100.100.100:3535:login:password",
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Тipo |  Descrição
----- | ----- | ----- 
`saveSettings` | **boolean** | Sinaliza que as configurações foram salvas

### Exemplo de uma resposta {#response-example-body}

```json
{
    "saveSettings": true
}
```

### Erros SetSettings {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setSettings/{{apiTokenInstance}}"

payload = "{\r\n\t\"countryInstance\": \"pt-br\",\r\n\t\"webhookUrl\": \"https://mysite.comb.r\",\r\n\t\"delaySendMessagesMilliseconds\": 1000,\r\n\t\"markIncomingMessagesReaded\": \"no\",\r\n\t\"proxyInstance\": \"123.456.78.910:39898:qGKqCo:Jb26Xz\",\r\n\t\"outgoingWebhook\": \"yes\",\r\n\t\"stateWebhook\": \"yes\",\r\n\t\"incomingWebhook\": \"yes\",\r\n\t\"deviceWebhook\": \"no\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```