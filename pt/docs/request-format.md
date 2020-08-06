# Executando uma requisição

Para executar uma requisição para a `Green API`, você deve executar uma requisição do tipo GET ou POST no endereço:

```
https://api.green-api.com/waInstance{{idInstance}}/{{method}}/{{apiTokenInstance}}
```

O endereço de requisição é formado a partir do número da conta `idInstance` e da chave de acesso` apiTokenInstance`, que você deve obter primeiro em [Minha conta](https://cabinet.green-api.com.br), de acordo com a seção [Antes de iniciar](before-start.md#parameters).

O método API requerido descrito em [Documentação da API](api/index.md) é usado como o parâmetro `method`.

Exemplo de requisição para enviar uma mensagem usando o método [SendMessage](api/sending/SendMessage.md):

```
https://api.green-api.com/waInstance1234/SendMessage/bde035edae3fc00bc116bd112297908d8145e5ba8decc5d884
```

## Request Headers

A maioria das solicitações deve conter o Request Headers:

- `Content-Type` - `application/json`

Em alguns casos, os cabeçalhos podem diferir, por exemplo, para o método de envio de arquivos [SendFileByUpload](api/sending/SendFileByUpload.md)

## Debugging

Para depurar solicitações na Green API, é recomendável a leitura de seção [Depurando Métodos da API](postman-collection.md)
