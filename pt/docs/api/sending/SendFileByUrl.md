# SendFileByUrl

O método pretende enviar um arquivo a partir de uma URL.
A mensagem será adicionada à fila de envio.

A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de envio de mensagens](../send-messages-delay.md).

Os arquivos de vídeo, áudio e imagem são enviados como no WhatsApp nativo, com a capacidade de visualizar e ouvir.
Os documentos são enviados da mesma maneira que no WhatsApp nativo. O tipo de arquivo a ser enviado e como enviá-lo será determinado pela extensão do arquivo.

> O tamanho máximo dos arquivos enviados é de 37 MB.

## Solicitação {#request}

Para enviar o arquivo, você deve utilizar a chamada da API conforme exemplo abaixo:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendFileByUrl/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

Parâmetro | Tipo | Obrigatório | Descrição
----- | ----- | ----- | -----
`chatId` | **string** | Sim | [ID do Grupo](../chat-id.md)
`urlFile` | **string** | Sim | Link para o arquivo a ser enviado
`fileName` | **string** | Sim | O nome do arquivo. Deve conter a extensão do arquivo
`caption` | **string** | Não | Descrição abaixo do arquivo. Descrição é adicionada a vídeos, imagens e documentos

### Exemplo de uma requisição {#request-example-body}

Envio de uma mensagem para um contato em particular:
```json
{
    "chatId": "5521999990000@c.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Isso é um cavalo"
}
```

Envio de uma mensagem para um grupo:
```json
{
    "chatId": "5521999990000-1581234048@g.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Isso é um cavalo"
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmentro | Tipo |  Descrição
----- | ----- | ----- 
`idMessage ` | **string** | ID da Mensagem Enviada 

### Exemplo de uma resposta {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Erros SendFileByUrl {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Código de exemplo Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/sendFileByUrl/{{apiTokenInstance}}"

payload = "{\r\n   \t\"chatId\": \"5521999990000@c.us\",\r\n\t\"urlFile\": \"https://my.site.com/img/horse.png\",\r\n\t\"fileName\": \"horse.png\",\r\n\t\"caption\": \"Isso é um cavalo\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```