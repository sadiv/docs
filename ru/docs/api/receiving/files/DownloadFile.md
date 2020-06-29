# DownloadFile

Метод предназначен для скачивания принятых и отправленных файлов аккаунтами.
Ссылки на принятые файлы передаются в webhook уведомлениях, а также их можно получить методом lastIncomingMessages.
Ссылки на отправленные файлы можно получить методом lastOutgoingMessages.
Срок хранения принятых файлов и соответственно возможность их скачивания ограничено 24 часами.

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`idMessage` | **string** | Да | Идентификатор сообщения, передаваемый в webhook уведомлениях или при отправки файлов методами sendFileByUrl || sendFileByUpload. Данный параметр передаётся как завершающая часть url запроса

## Ответ {#response}

Файл из сообщения

### Ошибки DownloadFile {#errors}

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `instance in starting process try later` | Аккаунт находится в процессе запуска/перезапуска. Попробуйте повторить попытку спустя несколько секунд.
400 | `instance account not authorized` | Аккаунт не авторизован. Для авторизации аккаунта перейдите в [Личный кабинет](https://cabinet.green-api.com) и считайте QR-код из приложения `WhatsApp Business` на телефоне.
400 | `bad request data` | Данные запроса не валидны. Исправьте ошибку в параметрах запроса и повторите попытку.

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/downloadFile/{{idMessage}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```