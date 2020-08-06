# LastIncomingMessages

O método retorna as últimas mensagens recebidas da conta.

> O período de armazenamento para mensagens recebidas no servidor é de 24 horas.

## Solicitação {#request}

Para retornar as últimas mensages recebidas, você deve utilizar a chamada da API conforme exemplo abaixo:

```
GET https://api.green-api.com/waInstance{{idInstance}}/LastIncomingMessages/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`idMessage` | **string** | [ID do Contato](../chat-id.md) da mensagem recebida
`timestamp` | **integer** | Horário de recepção da mensagem UNIX
`typeMessage` | **string** | Tipo de mensagem, valores possíveis:
| | `textMessage` - mensagem de texto
| | `imageMessage` - mensagem com imagem
| | `videoMessage` - mensagem com vídeo
| | `documentMessage` - mensagem com arquivo de documento
| | `audioMessage` - mensagem de áudio
| | `locationMessage` - messagem de geo-localização
| | `contactMessage` - mensagem de um contato anexado
| | `extendedTextMessage` - mensagem com link de visualização
`chatId` | **string** | [ID do Contato](../chat-id.md), em que a mensagem foi recebida
`senderId` | **string** | [ID do Contato](../chat-id.md#corr) remetente da mensagem
`senderName` | **string** | Nome do Remetente
`textMessage` | **string** | O texto da mensagem se `typeMessage`=`textMessage`
`downloadUrl` | **string** | Link para baixar o arquivo se `typeMessage` =` imageMessage` / `videoMessage` /` documentMessage` / `audioMessage`
`caption` | **string** | Descrição do Arquivo
`location` | **object** | Objeto contendo a geo-localização
`contact` | **object** | Objeto contento um contato
`extendedTextMessage` | **object** | Objeto contendo um link

Objeto contendo a geo-localização - `location`:

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`nameLocation` | **string** | Nome do Local
`address` | **string** | Endereço de localização
`latitude` | **double** | Latitude de localização
`longitude` | **double** | Longitude de localização
`jpegThumbnail` | **string** | Visualizar imagem na codificação `base64`

Objeto contendo contato - `contact`:

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`displayName` | **string** | Nome de exibição do contato
`vcard` | **string** | Estrutura do VCard (cartão de visita de contato)

Objeto contendo um link - `extendedTextMessage`:

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`text` | **string** | Texto do link
`description` | **string** | Descrição do Link
`title` | **string** | Título do link
`previewType` | **string** | Tipo de visualização do link
`jpegThumbnail` | **string** | Visualizar imagem na codificação `base64`

### Exemplo de uma resposta {#response-example-body}

```json
[
    {
        "idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
        "timestamp": 1587129319,
        "typeMessage": "textMessage",
        "chatId": "552198888000001c.us",
        "senderId": "55219888800001@c.us",
        "senderName": "Carlos",
        "textMessage": "Oi, tudo bem"
    },
    {
        "idMessage": "EA0BD1AE042DC4F3609867126309D67C",
        "timestamp": 1587147598,
        "typeMessage": "imageMessage",
        "chatId": "55219888800002@c.us",
        "senderId": "55219888800002@c.us",
        "senderName": "José",
        "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/EA1BD1AE042DC4F3609867126309D67C",
        "caption": "Pegue esse arquivo ai!"
    }
]
```

### Erros LastIncomingMessages {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/lastIncomingMessages/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```