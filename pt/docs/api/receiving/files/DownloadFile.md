# DownloadFile

O método é destinado ao download de arquivos recebidos e enviados..
Os links para os arquivos recebidos são transmitidos em [Mensagem recebida](../notifications-format/incoming-message/Webhook-IncomingMessageReceived.md) e também podem ser obtidos usando o método [LastIncomingMessages](../../../api/journals/LastIncomingMessages.md).
Os links para os arquivos enviados podem ser obtidos usando o método [LastOutgoingMessages](../../../api/journals/LastOutgoingMessages.md).

> Os arquivos estarão disponíveis para download é de até 24 horas.

## Solicitação {#request}

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`idMessage` | **string** | Sim | Identificador de mensagem transmitido em [Mensagem recebida](../notifications-format/incoming-message/Webhook-IncomingMessageReceived.md) ou ao enviar arquivos usando os métodos [SendFileByUrl](../../../api/sending/SendFileByUrl.md), [SendFileByUpload](../../../api/sending/SendFileByUpload.md)). Este parâmetro é passado como a parte final do URL da requisição

## Resposta {#response}

Arquivo da mensagem

### Erros DownloadFile {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/downloadFile/{{idMessage}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```