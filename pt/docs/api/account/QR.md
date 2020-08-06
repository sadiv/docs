# QR

O método foi projetado para ler o QR code.
Para autorizar sua conta, você precisa ler o QR code como no aplicativo [WhatsApp Business](https://www.whatsapp.com/business/) do seu telefone.
Você também pode obter um código QR e autorizar em sua conta pessoal. O procedimento para autorizar sua conta por meio de sua conta pessoal está descrito na seção [Antes de começar](../../before-start.md#qr).

> O QR code é atualizado a cada 20 segundos; portanto, é recomendável chamar o método para receber o QR code com um intervalo de 5 segundos.

Para receber um código QR, a instância deve estar com status Não Autorizado. Se a instância estiver autorizada, você deve primeiro desconectá-la usando o método [Logout](Logout.md).

Após a digitalização bem-sucedida do código QR e a autorização da conta, uma [notificação de entrada](../receiving/index.md) é gerada com o formulário [Status da conta](../receiving/notifications-format/StateInstanceChanged.md).

> Você também pode obter um código QR via [WebSocket](Scanqrcode.md)

## Requisição {#request}

Para efetuar a leitura do QR code, você deve utilizar a chamada da API conforme exemplo abaixo:
```
GET https://api.green-api.com/waInstance{{idInstance}}/qr/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).


## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`type` | **string** | Tipo de mensagem, valores possíveis `qrCode`, `error`, `alreadyLogged`
`message` | **string** | Conteúdo da mensagem. Aceita valores diferentes, dependendo do valor do campo `type`


#### Imagem do QR code recebida {#response-type-qrCode}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`type` | **string** | `qrCode` - imagem recebida do QR code
`message` | **string** | Imagem de QR code codificado em Base64. Para exibir no navegador, adicione a linha `data:image/png;base64, {message}`

#### Tipos de Erros {#response-type-error}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`type` | **string** | `error` - Ocorreu um erro
`message` | **string** | Descrição do Erro


#### Conta já conectada {#response-type-alreadyLogged}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`type` | **string** | `alreadyLogged` - conta já está autorizada. Para receber um novo QR code, você deve primeiro sair da sua conta usando o método [Logout](Logout.md)
`message` | **string** | Recebe o valor `instance account already authorized`


### Erros QR {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de recebimento do QR code no browser {#request-example-js}

```js
// ...
```

Um exemplo de recebimento de um QR code em um browser pode ser visto em [browserExample](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExample.html) 

## Código Python de exemplo  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/qr/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
