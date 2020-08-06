# GetDeviceInfo

O método foi desenvolvido para obter informações sobre o dispositivo (telefone) no qual o aplicativo [WhatsApp Business](https://www.whatsapp.com/business/) está sendo executado.

## Solicitação {#request}

Para acessar informações sobre o dispositivo, você deve utilizar a chamada da API conforme exemplo abaixo:

```
GET https://api.green-api.com/waInstance{{idInstance}}/GetDeviceInfo/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#params).

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

Parâmetro | Tipo | Descrição
----- | ----- | ----- 
`platform` | **string** | O sistema operacional do dispositivo no qual o aplicativo está sendo executado [WhatsApp Business](https://www.whatsapp.com/business/)
`deviceManufacturer` | **string** | Fabricante do dispositivo
`deviceModel` | **string** | Modelo do dispositivo
`osVersion` | **string** | Versão do sistema operacional
`waVersion` | **string** | Versão do aplicativo [WhatsApp Business](https://www.whatsapp.com/business/) ou [WhatsApp](https://www.whatsapp.com/)
`battery` | **integer** | Nível de bateria

### Exemplo de uma resposta {#response-example-body}

```json
{
    "platform": "iphone",
    "deviceManufacturer": "Apple",
    "deviceModel": "iPhone 11",
    "osVersion": "13.4.1",
    "waVersion": "2.20.42",
    "battery": 90
}
```

### Erros GetDeviceInfo {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## Exemplo de código Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getDeviceInfo/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```