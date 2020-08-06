# Scanqrcode

Além de receber um QR code usando o método [QR](QR.md), também possível fazer via conexão de websocket. O tempo de espera para digitalizar um QR code é de 100 segundos. Durante esse período, o QR code deve ser digitalizado. Para receber um QR code, a conta deve estar em status não autorizado. Se a conta estiver autorizada, você deve primeiro desconectá-la usando o método [Logout](Logout.md)

Após a digitalização bem-sucedida do QR code e a autorização da conta, uma [notificação de entrada](../receiving/index.md) é gerada com o formulário [Status da conta] (../ recebendo / notificações-formato / StateInstanceChanged.md).

Você precisa estabelecer uma conexão de websocket em: 

```
wss://api.green-api.com/waInstance{{idInstance}}/scanqrcode/{{apiTokenInstance}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`type` | **string** | Tipo de mensagem, valores possíveis `qrCode`, `error`, `accountData`, `alreadyLogged`, `timeoutExpired`
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


#### O tempo limite da verificação do QR code expirou {#response-type-timeoutExpired}

Parâmetro | Tipo |  Descrição
----- | ----- | ----- 
`type` | **string** | `timeoutExpired` - passou o tempo durante o qual o QR code deve ser verificado. O tempo limite de espera para digitalizar é de 100 segundos.
`message` | **string** | Recebe o valor `timeoutExpired`

#### Dados da conta autorizados recebidos {#response-type-accountData}

Поле | Тип |  Описание
----- | ----- | ----- 
`type` | **string** | `accountData` - dados da conta recebidos após autorização bem-sucedida
`wid` | **string** | ID da conta no formato WhatsApp
`pushname` | **string** | Nome da conta do WhatsApp
`proxy` | **string** |  Endereço IP do proxy atribuído à conta
`webhookUrl` | **string** | URL para receber notificações recebidas

### Código Exemplo em Python para se Obter via Websocket

```python
from websocket import create_connection

ws = create_connection("wss://api.green-api.com/waInstance{{idInstance}}/scanqrcode/{{apiTokenInstance}")

print("Sending 'Give me the code!'...")
ws.send("Give the code")
print("Sent")
print("Receiving...")
result =  ws.recv()
print("This is the code '%s'" % result)
ws.close()
```


