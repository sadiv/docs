# API documents

Green API presents HTTP API WhatsApp for sending and receiving messages, files, working with group chats, getting contacts and other methods. 

Make sure you have completed all the steps in [Before you start](../before-start.md) section before executing requests. Check out [Requests execution](../request-format.md) section. Use [Postman collection](../postman-collection.md) to debug requests to Green API. 

## [Account](./account/index.md) {#account}

- [Get account settings](./account/GetSettings.md)
- [Set account settings](./account/SetSettings.md)
- [Set system proxy](./account/SetSystemProxy.md)
- [Get account state](./account/GetStateInstance.md)
- [Reboot account](./account/Reboot.md)
- [Logout account](./account/Logout.md)
- [Get QR code](./account/QR.md)
- [Get QR code via websocket](./account/Scanqrcode.md)

## [Sending](./sending/index.md) {#sending}

- [Send text message](./sending/SendMessage.md)
- [Send ordinary buttons](./sending/SendButtons.md)
- [Send template buttons](./sending/SendTemplateButtons.md)
- [Send list message](./sending/SendListMessage.md)
- [Send video, audio, image, document](./sending/SendFileByUpload.md)
- [Send video, audio, image, document by URL](./sending/SendFileByUrl.md)
- [Send location](./sending/SendLocation.md)
- [Send contact](./sending/SendContact.md)
- [Send link](./sending/SendLink.md)

## [Receiving](./receiving/index.md) {#receiving}

### [Receiving notifications via HTTP API](receiving/technology-http-api.md) {#technology-http-api}
- [Receive notification](receiving/technology-http-api/ReceiveNotification.md)
- [Delete notification](receiving/technology-http-api/DeleteNotification.md)

### [Receiving notofications via Webhook Endpoint](receiving/technology-webhook-endpoint.md) {#technology-webhook-endpoint}

### [Incoming notifications format](receiving/notifications-format/index.md) {#notifications-format}

#### [Incoming message](receiving/notifications-format/incoming-message/Webhook-IncomingMessageReceived.md) {#receiving-incoming-message}

- [Incoming text message](./receiving/notifications-format/incoming-message/TextMessage.md)
- [Ordinary button selection](./receiving/notifications-format/selected-buttons/ButtonsResponseMessage.md)
- [Template button selection](./receiving/notifications-format/selected-buttons/TemplateButtonsReplyMessage.md)
- [List element selection](./receiving/notifications-format/selected-buttons/ListResponseMessage.md)
- [Incoming text message with URL](./receiving/notifications-format/incoming-message/ExtendedTextMessage.md)
- [Incoming image, video, audio, document message](./receiving/notifications-format/incoming-message/ImageMessage.md)
- [Incoming location message](./receiving/notifications-format/incoming-message/LocationMessage.md)
- [Incoming contact message](./receiving/notifications-format/incoming-message/ContactMessage.md)

#### Outgoing message {#receiving-outgoing-message}

- [Message sent from phone](./receiving/notifications-format/outgoing-message/OutgoingMessage.md)
- [Message sent via API](./receiving/notifications-format/outgoing-message/OutgoingApiMessage.md)
- [Sent message status](./receiving/notifications-format/outgoing-message/OutgoingMessageStatus.md)

#### Others {#receiving-dif}

- [Account status](./receiving/notifications-format/StateInstanceChanged.md)
- [Device status](./receiving/notifications-format/DeviceInfo.md)
- [Incoming call](./receiving/notifications-format/IncomingCall.md)

#### Objects {#receiving-obj}

- [Incoming notifications types](./receiving/notifications-format/type-webhook.md)

### Receiving files {#receiving-files}

- [Download file from an incoming message](./receiving/files/DownloadFile.md)


## [Journals](./journals/index.md) {#journals}

- [Get chat messages history](./journals/GetChatHistory.md)
- [Get incoming messages journal](./journals/LastIncomingMessages.md)
- [Get outgoing messages journal](./journals/LastOutgoingMessages.md)

## [Queues](./queues/index.md) {#queues}

- [Get messages queue](./queues/ShowMessagesQueue.md)
- [Clear messages queue](./queues/ClearMessagesQueue.md)

## [Groups](./groups/index.md) {#groups}

- [Create a group](./groups/CreateGroup.md)
- [Change group name](./groups/UpdateGroupName.md)
- [Get group info](./groups/GetGroupData.md)
- [Add group participant](./groups/AddGroupParticipant.md)
- [Remove group participant](./groups/RemoveGroupParticipant.md)
- [Set group admin rights](./groups/SetGroupAdmin.md)
- [Remove group admin rights](./groups/RemoveAdmin.md)
- [Leave group](./groups/LeaveGroup.md)

## [Read mark](./marks/index.md) {#marks}

- [Mark chat read](./marks/ReadChat.md)

## [Device (phone)](./phone/index.md) {#phone}

- [Get device info](./phone/GetDeviceInfo.md)

## [Service methods](./service/index.md) {#service}

- [Check WhatsApp availability](./service/CheckWhatsapp.md)
- [Get avatar](./service/GetAvatar.md)
- [Get contacts](./service/GetContacts.md)

## Other {#dif}

- [Chat Id](chat-id.md)
- [Messages sending delay](send-messages-delay.md)
- [Common errors](common-errors.md)
