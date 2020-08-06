# Documentação da API

Green API fornece a API HTTP do WhatsApp para enviar e receber mensagens, arquivos, trabalhar com bate-papos em grupo, obter uma lista de contatos e outros métodos.

Antes de executar as consultas, verifique se todas as etapas na seção [Antes de começar](../before-start.md) foram concluídas. Confira a seção [Executando uma consulta](../request-format.md).
Para debugar as solicitações na Gren API, use a seção [Utilizando o Postman](../postman-collection.md).

## [Conta](./account/index.md) {#account}

- [Acessando a Configuração da Conta](./account/GetSettings.md)
- [Definindo as configurações da sua Conta](./account/SetSettings.md)
- [Obtendo o status de sua Conta](./account/GetStateInstance.md)
- [Reiniciando sua Conta](./account/Reboot.md)
- [Efetuando um logout de sua Conta](./account/Logout.md)
- [Autorizando o acesso via QR code](./account/Scanqrcode.md)

## [Envio de Mensagens](./sending/index.md) {#sending}

- [Enviando mensagens de texto](./sending/SendMessage.md)
- [Enviando vídeo, audio, imagens e documentos](./sending/SendFileByUpload.md)
- [Enviando vídeo, audio, imagens e documentos através de uma URL](./sending/SendFileByUrl.md)
- [Enviando geo-localização](./sending/SendLocation.md)
- [Enviando contatos](./sending/SendContact.md)
- [Enviando links](./sending/SendLink.md)

## [Recebendo Respostas](./receiving/index.md) {#receiving}

### Webhook {#receiving-webhook}

#### [Mensagens Recebidas](./receiving/notifications-format/incoming-message/Webhook-IncomingMessageReceived.md) {#receiving-incoming-message}

- [Mensagem de Texto Recebida](./receiving/notifications-format/incoming-message/TextMessage.md)
- [Mensagem de texto recebida com URL](./receiving/notifications-format/incoming-message/ExtendedTextMessage.md)
- [Mensagem recebida com imagem, vídeo, áudio, documento](./receiving/notifications-format/incoming-message/ImageMessage.md)
- [Mensagem recebida com geolocalização](./receiving/notifications-format/incoming-message/LocationMessage.md)
- [Mensagem recebida com contato](./receiving/notifications-format/incoming-message/ContactMessage.md)

#### Mensagens Enviadas {#receiving-outgoing-message}

- [Status da Mensagem enviada](./receiving/notifications-format/outgoing-message/OutgoingMessageStatus.md)

#### Outros {#receiving-dif}

- [Status da Conta](./receiving/notifications-format/StateInstanceChanged.md)
- [Status do Dispositivo](./receiving/notifications-format/DeviceInfo.md)

### Objetos

- [Tipo de notifações do Webhook](./receiving/notifications-format/type-webhook.md)

### Recebendo arquivos {#receiving-files}

- [Download de arquivos de mensagens recebidas](./receiving/files/DownloadFile.md)

## [Listas de Mensagens](./journals/index.md) {#journals}

- [Obter log da Caixa de Entrada](./journals/LastIncomingMessages.md)
- [Obter log das mensagens enviadas](./journals/LastOutgoingMessages.md)

## [Filas de Envio](./queues/index.md) {#queues}

- [Obter a fila de mensagens a serem enviadas](./queues/ShowMessagesQueue.md)
- [Limpar fila de mensagens para envio](./queues/ClearMessagesQueue.md)

## [Grupos](./groups/index.md) {#groups}

- [Como criar um grupo](./groups/CreateGroup.md)
- [Alterar o nome do grupo](./groups/UpdateGroupName.md)
- [Obter informações do grupo](./groups/GetGroupData.md)
- [Adicionar o membro ao Grupo](./groups/AddGroupParticipant.md)
- [Remover Membro do Grupo](./groups/RemoveGroupParticipant.md)
- [Atribuir Direitos de Administrador do Grupo](./groups/SetGroupAdmin.md)
- [Revogar direitos de administrador do grupo](./groups/RemoveAdmin.md)
- [Sair do Grupo](./groups/LeaveGroup.md)

## [Leitura da Mensagem](./marks/index.md) {#marks}

- [Marcar conversa como lida](./marks/ReadChat.md)

## [Dispositivo (telefone)](./phone/index.md) {#phone}

- [Obter informações do dispositivo](./phone/GetDeviceInfo.md)

## [Métodos de Serviço](./service/index.md) {#service}

- [Verificando se é uma conta WhatsApp](./service/CheckWhatsapp.md)
- [Obtendo Imagem do Perfil](./service/GetAvatar.md)
- [Obter contatos](./service/GetContacts.md)

## Outros {#dif}

- [ID da Conversa](chat-id.md)
- [Intervalo de Envio de Mensagens](send-messages-delay.md)
- [Erros Comuns](common-errors.md)
