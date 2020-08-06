# Intervalo de envio de mensagens

Ao enviar mensagens ou arquivos, todos os dados estão na fila para envio. Todas as mensagens são enviadas da fila seqüencialmente em ordem de recebimento na fila (FIFO).
Isso define o intervalo entre o envio de mensagens da fila. Para alterar o intervalo para o envio de mensagens, use o método [SetSettings](account/SetSettings.md) e o parâmetro `delaySendMessagesMilliseconds`.

O intervalo mínimo de envio de mensagens é de 500 ms.

Você pode visualizar o intervalo de envio atual usando o método [GetSettings](account/GetSettings.md), com o parâmetro `delaySendMessagesMilliseconds`.

## Alterar intervalo de envio de mensagens

Para alterar o intervalo para o envio de mensagens, você deve realizar uma requisição usando o método abaixo:

```
POST https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}
```

Adicione o parâmetro `delaySendMessagesMilliseconds` dentro no corpo POST para realizar a alteração.

### Exemplo sobre como definir o intervalo de envio para 5 segundos

```json
{
    "delaySendMessagesMilliseconds": 5000
}
```

### Exemplo de código em Python {# request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}"

payload = "{\r\n\t\"delaySendMessagesMilliseconds\": 5000\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```