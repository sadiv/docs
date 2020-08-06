# DeleteNotification

O método visa remover uma notificação de entrada da fila de notificações. Use o parâmetro `receiptId` para especificar qual notificação excluir.
Depois de receber e processar a notificação recebida, você precisa excluir a notificação da fila. Depois de chamar o método, a notificação será considerada aceita e processada e será excluída permanentemente da fila. Dessa forma, a próxima chamada ao método [ReceiveNotification](ReceiveNotification.md) retornará a próxima notificação da fila na ordem em que as notificações são recebidas.

> O período de armazenamento de notificações recebidas na fila é de 24 horas.

> Notificações sao recebidas de fora da fila na ordem [FIFO](https://pt.wikipedia.org/wiki/FIFO)

## Requisição {#request}

Para remover uma notificação de entrada da fila, você precisa fazer uma chamada de API conforme o exemplo abaixo:
```
DELETE https://api.green-api.com/waInstance{{idInstance}}/DeleteNotification/{{apiTokenInstance}}/{{receiptId}}
```

> Observe que você precisa usar a solicitação de tipo `DELETE`

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../../before-start.md#parameters).

### Parâmetros de Consulta {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`receiptId` | **integer** | Sim | ID da entrega para excluir uma notificação recebida obtida pelo método [ReceiveNotification](ReceiveNotification.md)


## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | -----
`result ` | **boolean** | Resultado da exclusão da notificação recebida: `true` - notificação recebida excluída da fila com êxito; `false` - notificação não excluída - possivelmente quando a notificação foi excluída anteriormente, ou 'receiptId` não corresponde ao valor obtido anteriormente pelo método [ReceiveNotification](ReceiveNotification.md)


### Exemplo de Reposta {#response-example-body}

```json
{
    "result": true
}
```

### Erros DeleteNotification {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../../common-errors.md)

Código HTTP | Identificador de erro | Descrição
----- | ----- | -----
400 | `Parameter receiptId must be a Number` | O parâmetro `receiptId` não está especificado ou contém caracteres não numéricos
400 | `Parameter idInstance not an integer` | O parâmetro `idInstance` não está especificado ou contém caracteres não numéricos
400 | `Parameter apiTokenInstance not define` | Nenhum parâmetro `apiTokenInstance` especificado


## Código Exemplo em Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/DeleteNotification/{{apiTokenInstance}}/1234567"

payload = {}
headers= {}

response = requests.request("DELETE", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

Exemplo de código de notificação em [NodeJS](https://nodejs.org) pode ser visualizado no arquivo [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js)