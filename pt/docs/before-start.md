# Antes de Começar

Antes de começar a trabalhar com a API Verde, você deve concluir as seguintes etapas:

1. [Crie uma conta em nosso painel](#cabinet)
2. [Crie uma instância de uso](#account)
3. [Instalar o aplicativo WhatsApp Business](#mobile)
4. [Autorizar conta do WhatsApp](#qr)
5. [Obter configurações de acesso à conta](#parameters)
6. [Configurar o recebimento de dados](#receiving)

## 1. Crie uma conta em nosso painel {#cabinet}

Para criar uma conta, vá para [Minha conta](https://cabinet.green-api.com.br). Após a autorização, sua conta estará disponível para criar uma instância. Na sua conta pessoal, você pode criar várias instâncias para uma conta.

## 2. Crie uma instância de uso {#account}

Uma instância é criada em sua conta e é disponibilizada para acessar a API HTTP do WhatsApp. Uma instância pode servir apenas um número de telefone por vez (uma conta do WhatsApp). Ao criar uma conta, você deve selecionar uma tarifa.

## 3. Instale o aplicativo WhatsApp Business {#mobile}

O envio e o recebimento de mensagens do WhatsApp são feitos no seu celular. Um aplicativo oficial [WhatsApp Business](https://www.whatsapp.com/business/) deve ser instalado no telefone. Também é possível usar o aplicativo [WhatsApp](https://www.whatsapp.com/) se o uso do [WhatsApp Business](https://www.whatsapp.com/business/) for inviável.

## 4. Autorizar conta do WhatsApp {#qr}

Se você usa um telefone celular pessoal para trabalhar com a Green API, precisa autorizar sua conta WhatsApp. A autorização da conta é realizada em [Minha conta](https://cabinet.green-api.com.br) lendo o código QR do aplicativo [WhatsApp Business](https://www.whatsapp.com/business/). Para fazer isso, abra o aplicativo [WhatsApp Business](https://www.whatsapp.com/business/) no seu celular, vá para as configurações do aplicativo e leia o código QR que é exibido na tela.

- Android: `WhatsApp Business` -> `Menu suspenso` -> `WhatsApp Web`
- iPhone: `WhatsApp Business` ->` Configurações` -> `WhatsApp Web` ->` Digitalizar código QR`

> O envio e recebimento de mensagens é realizado no seu celular. Portanto, o telefone sempre deve ser carregado e conectado à Internet.

## 5. Obtenha os parâmetros de acesso à instância {#parameters}

Para executar solicitações da API HTTP do WhatsApp, você precisa usar as configurações de acesso à instância. Os parâmetros de acesso são publicados em [Minha conta](https://cabinet.green-api.com.br):

- `idInstance` - Código de acesso exclusivo da Instância
- `apiTokenInstance` - Chave de Acesso à Instância

A chave de acesso à conta pode ser alterada se necessário.

## Tudo Pronto!

Está tudo pronto para começar a enviar e receber mensagens do WhatsApp!

Para depurar solicitações na Green API, é recomendável acessar a seção [Depurando métodos da API](postman-collection.md)