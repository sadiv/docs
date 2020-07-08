# Документация API

Green API предоставляет HTTP API WhatsApp для отправки и получения сообщений, файлов, работы с групповыми чатами, получения списка контактов и других методов.

Перед выполнением запросов убедитесь, что выполнены все шаги раздела [Перед началом работы](/before-start). Ознакомьтесь с разделом [Выполнение запросов](/request-format). Для отладки запросов к Green API воспользуйтесь [Коллекцией Postman](/postman-collection).

## [Аккаунт](/api/account/) {#account}

- [Получить настройки аккаунта](/api/account/GetSettings)
- [Установить настройки аккаунта](/api/account/SetSettings)
- [Получить состояние аккаунта](/api/account/GetStateInstance)
- [Перезапустить аккаунт](/api/account/Reboot)
- [Разлогинить аккаунт](/api/account/Logout)
- [Авторизовать аккаунт (через websocket)](/api/account/Scanqrcode)

## [Отправка](/api/sending/) {#sending}

- [Отправить текст](/api/sending/SendMessage)
- [Отправить видео, аудио, изображение, документ](/api/sending/SendFileByUpload)
- [Отправить видео, аудио, изображение, документ по URL](/api/sending/SendFileByUrl)
- [Отправить геолокацию](/api/sending/SendLocation)
- [Отправить контакт](/api/sending/SendContact)
- [Отправить ссылку](/api/sending/SendLink)

## [Получение](/api/receiving/) {#receiving}

### Webhook {#receiving-webhook}

#### [Входящее сообщение](/api/receiving/webhook/incoming-message/Webhook-IncomingMessageReceived) {#receiving-incoming-message}

- [Входящее текстовое сообщение](/api/receiving/webhook/incoming-message/TextMessage)
- [Входящее текстовое сообщение с URL](/api/receiving/webhook/incoming-message/ExtendedTextMessage)
- [Входящее сообщение с изображением, видео, аудио, документом](/api/receiving/webhook/incoming-message/ImageMessage)
- [Входящее сообщение с геолокацией](/api/receiving/webhook/incoming-message/LocationMessage)
- [Входящее сообщение с контактом](/api/receiving/webhook/incoming-message/ContactMessage)

#### Отправленное сообщение {#receiving-outgoing-message}

- [Статус отправленного сообщения](/api/receiving/webhook/outgoing-message/OutgoingMessageStatus)

#### Прочие {#receiving-dif}

- [Статус аккаунта](/api/receiving/webhook/StateInstanceChanged)
- [Статус устройства](/api/receiving/webhook/DeviceInfo)

### Получение файлов {#receiving-files}

- [Скачать файл из входящего сообщения](/api/receiving/files/DownloadFile)

## [Журналы](/api/journals/) {#journals}

- [Получить журнал входящих сообщений](/api/journals/LastIncomingMessages)
- [Получить журнал отправленных сообщений](/api/journals/LastOutgoingMessages)

## [Очереди](/api/queues/) {#queues}

- [Получить очередь сообщений к отправке](/api/queues/ShowMessagesQueue)
- [Очистить очередь сообщений к отправке](/api/queues/ClearMessagesQueue)

## [Группы](/api/groups/) {#groups}

- [Создать группу](/api/groups/CreateGroup)
- [Изменить имя группы](/api/groups/UpdateGroupName)
- [Получить информацию о группе](/api/groups/GetGroupData)
- [Добавить участника в группу](/api/groups/AddGroupParticipant)
- [Удалить участника из группы](/api/groups/RemoveGroupParticipant)
- [Назначить права администратора группы](/api/groups/SetGroupAdmin)
- [Отозвать права администратора группы](/api/groups/RemoveAdmin)
- [Выйти из группы](/api/groups/LeaveGroup)

## [Отметка прочтения](/api/marks/) {#marks}

- [Отметить чат прочитанным](/api/marks/ReadChat)

## [Устройство (телефон)](/api/phone/) {#phone}

- [Получить информацию об устройстве](/api/phone/GetDeviceInfo)

## [Сервисные методы](/api/service/) {#service}

- [Проверить наличие WhatsApp](/api/service/CheckWhatsapp)
- [Получить аватар](/api/service/GetAvatar)
- [Получить контакты](/api/service/GetContacts)
