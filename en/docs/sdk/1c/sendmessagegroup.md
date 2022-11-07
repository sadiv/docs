# Как отправить текстовое сообщение в группу
### Установка
1. [Скачать обработку](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf) в формате epf
2. Подключиться к сервису через встроенный в обработку помощник или  самостоятельно через сайт [green-api.com](https://green-api.com/). Получить ``API Token`` и ``ID Instance``
3. Запустить в браузере или тонком клиенте и указать параметры подключения (``API Token`` и ``ID Instance``)
4. Сканировать QR код с мобильного телефона WhatsApp (Меню чаты -> Иконка всех функций -> Связанные устройства -> Привязка устройства)
6. В форме обработки нажать кнопку ``Проверить подключение``. Поле формы статус должно изменится на "Подключен"

![`Проверить подключение`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Login.png?raw=true)

### Использование обработки в собственных конфигурациях

Обработка имеет программный интерфейс, оформленный в соответствии со [стандартами разработки 1С](https://its.1c.ru/db/v8std). Вы можете встроить ее в свою конфигурацию и вызывать АПИ на сервере через создание объекта.

### Примеры

#### Как отправить текстовое сообщения используя обработку

![`Отправка сообщения`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Sending.png?raw=true)

1. Перейти на вкладку `Отправка сообщений`
2. Указать телефон получателя и текст соообщения
3. Нажать кнопку `Отправить текст`

#### Как отправить текстовое сообщения в группу используя собственную конфигурацию

```bsl
АПИ = Обработки.GreenAPI.Создать();
АПИ.IdInstance = "ВАШ_ИНСТАНС";
АПИ.ApiToken = "ВАШ_ТОКЕН";
Ответ = АПИ.ОтправитьТекстВГруппу("79001234567-1615394251@g.us", "Hello"); 
```
### Полный список примеров

Описание |  Модуль
----- | ----- 
Демо обработка 1С для WhatsApp| [GreenAPI.epf](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf)
Исходники обработки 1С для WhatsApp| [whatsapp-api-client-1c](https://github.com/green-api/whatsapp-api-client-1c)