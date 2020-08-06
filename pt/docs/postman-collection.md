# Depurando Métodos da API

Para solicitações de teste e depuração da Green API, é recomendável usar a [Green API - Postman Collection](https://github.com/green-api/green-api-postman-collection)

[Postman](https://www.getpostman.com/) é uma ferramenta popular para testar e desenvolver APIs. Para facilitar a integração dos desenvolvedores com a Green API, criamos um Postman Collection com o conjunto completo com todos os métodos de nossa API.

1. [Instalação](#setup): instala o collection
2. [Configuração](#configure): configurando variáveis ​​de ambiente
3. [Teste](#test): usando métodos API

## Instalação {#setup}

Para começar, baixe os seguintes componentes e instale o Postman:

- Aplicativo [Postman](https://www.postman.com/downloads/)
- Postman Collection [Green API - Postman Collection](https://github.com/green-api/green-api-postman-collection) (clone o repositório ou faça o download do pacote como um arquivo ZIP)

Após instalar e iniciar o Postman, clique em `Import` e selecione os dois arquivos JSON `collection.json` e `environment.json` no repositório Postman Collection no GitHub. Após a importação, você verá o elemento `Green API` na seção` Collections` e poderá selecionar o item `Green API Developer` como o` Environment`.

## Configuração {#configure}

O ambiente personalizado do Postman é na verdade uma coleção de pares de valores-chave. Você pode criar variáveis ​​padrão que serão usadas em diferentes consultas. [Mais sobre variáveis ​​de ambiente do Postman](https://learning.postman.com/docs/postman/variables-and-environments/managing-environments/).

O ambiente `Green API Developer` pré-configurado contém um conjunto completo de variáveis ​​referenciadas pela coleção. Algumas dessas variáveis ​​devem ser editadas e substituídas por seus próprios valores. Para abrir a caixa de diálogo de edição, clique no botão pequeno com a imagem do olho ao lado da lista suspensa do ambiente e selecione `Edit`.

Defina os valores das duas variáveis ​​`idInstance` e` apiTokenInstance`, que foram obtidas no estágio [Antes de iniciar](before-start.md#parameters).

## Testando {#test}

Agora você pode selecionar qualquer método de API na coleção e começar a enviar solicitações. Por conveniência, todos os métodos estão listados na mesma ordem em que são descritos em [Documentação da API](api/index.md). Você pode fazer alterações nesses métodos para simplificar seus testes e processamento de respostas.