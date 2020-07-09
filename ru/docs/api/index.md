# Документация API

Green API предоставляет HTTP API WhatsApp для отправки и получения сообщений, файлов, работы с групповыми чатами, получения списка контактов и других методов.

Перед выполнением запросов убедитесь, что выполнены все шаги раздела [Перед началом работы](../before-start.md). Ознакомьтесь с разделом [Выполнение запросов](../request-format.md). Для отладки запросов к Green API воспользуйтесь [Коллекцией Postman](../postman-collection.md).

## [Аккаунт](./account/index.md) {#account}

- [Получить настройки аккаунта](./account/GetSettings.md)
- [Установить настройки аккаунта](./account/SetSettings.md)
- [Получить состояние аккаунта](./account/GetStateInstance.md)
- [Перезапустить аккаунт](./account/Reboot.md)
- [Разлогинить аккаунт](./account/Logout.md)
- [Авторизовать аккаунт (через websocket)](./account/Scanqrcode.md)

## [Отправка](./sending/index.md) {#sending}

- [Отправить текст](./sending/SendMessage.md)
- [Отправить видео, аудио, изображение, документ](./sending/SendFileByUpload.md)
- [Отправить видео, аудио, изображение, документ по URL](./sending/SendFileByUrl.md)
- [Отправить геолокацию](./sending/SendLocation)
- [Отправить контакт](./sending/SendContact)
- [Отправить ссылку](./sending/SendLink)

## [Получение](./receiving/index.md) {#receiving}

### Webhook {#receiving-webhook}

#### [Входящее сообщение](./receiving/webhook/incoming-message/Webhook-IncomingMessageReceived.md) {#receiving-incoming-message}

- [Входящее текстовое сообщение](./receiving/webhook/incoming-message/TextMessage)
- [Входящее текстовое сообщение с URL](./receiving/webhook/incoming-message/ExtendedTextMessage)
- [Входящее сообщение с изображением, видео, аудио, документом](./receiving/webhook/incoming-message/ImageMessage)
- [Входящее сообщение с геолокацией](./receiving/webhook/incoming-message/LocationMessage)
- [Входящее сообщение с контактом](./receiving/webhook/incoming-message/ContactMessage)

#### Отправленное сообщение {#receiving-outgoing-message}

- [Статус отправленного сообщения](./receiving/webhook/outgoing-message/OutgoingMessageStatus)

#### Прочие {#receiving-dif}

- [Статус аккаунта](./receiving/webhook/StateInstanceChanged)
- [Статус устройства](./receiving/webhook/DeviceInfo)

### Получение файлов {#receiving-files}

- [Скачать файл из входящего сообщения](./receiving/files/DownloadFile)

## [Журналы](./journals/index.md) {#journals}

- [Получить журнал входящих сообщений](./journals/LastIncomingMessages)
- [Получить журнал отправленных сообщений](./journals/LastOutgoingMessages)

## [Очереди](./queues/index.md) {#queues}

- [Получить очередь сообщений к отправке](./queues/ShowMessagesQueue)
- [Очистить очередь сообщений к отправке](./queues/ClearMessagesQueue)

## [Группы](./groups/index.md) {#groups}

- [Создать группу](./groups/CreateGroup)
- [Изменить имя группы](./groups/UpdateGroupName)
- [Получить информацию о группе](./groups/GetGroupData)
- [Добавить участника в группу](./groups/AddGroupParticipant)
- [Удалить участника из группы](./groups/RemoveGroupParticipant)
- [Назначить права администратора группы](./groups/SetGroupAdmin)
- [Отозвать права администратора группы](./groups/RemoveAdmin)
- [Выйти из группы](./groups/LeaveGroup)

## [Отметка прочтения](./marks/index.md) {#marks}

- [Отметить чат прочитанным](./marks/ReadChat)

## [Устройство (телефон)](./phone/index.md) {#phone}

- [Получить информацию об устройстве](./phone/GetDeviceInfo)

## [Сервисные методы](./service/index.md) {#service}

- [Проверить наличие WhatsApp](./service/CheckWhatsapp)
- [Получить аватар](./service/GetAvatar)
- [Получить контакты](./service/GetContacts)
