# SendFileByUpload

O método é destinado ao envio de um arquivo carregado através de um form (form-data).
A mensagem será adicionada à fila de envio. A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de envio de mensagens](../send-messages-delay.md).

Os arquivos de vídeo, áudio e imagem são enviados como no WhatsApp nativo, com a capacidade de visualizar e ouvir.
Os documentos são enviados da mesma maneira que no WhatsApp nativo. O tipo de arquivo a ser enviado e como enviá-lo será determinado pela extensão do arquivo.

> O tamanho máximo dos arquivos enviados é de 37 MB.

## Solicitação {#request}

Para enviar o arquivo, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendFileByUpload/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do Grupo](../chat-id.md)
`file` | **file** | Sim | Arquivo Enviado
`caption` | **string** | Não | Descrição abaixo do arquivo. A Descrição é adicionada a vídeos, imagens e documentos.

### Exemplo de uma requisição {#request-example-body}

Código de exemplo Python

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendFileByUpload/{{apiTokenInstance}}"

payload = {'chatId': '5521999990000@c.us',
'caption': 'Descrição'}
files = [
  ('file', open('/C:/window.jpg','rb'))
]
headers= {}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

print(response.text.encode('utf8'))
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmentro | Tipo |  Descrição
----- | ----- | ----- 
`idMessage ` | **string** | ID da mensagem enviada

### Exemplo de uma resposta {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Erros SendFileByUpload {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)
