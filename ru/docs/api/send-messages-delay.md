# Интервал отправки сообщений

При отправке сообщений или файлов все данные помещаются в очередь на отправку. Все сообщения отправляются из очереди последовательно в порядке поступления в очередь (FIFO). При этом устанавливается интервал между отправкой сообщений из очереди. Для изменения интервала отправки сообщений предназначен метод [SetSettings](account/SetSettings.md) и параметр `delaySendMessagesMilliseconds`.

Минимальный интервал отправки сообщений составляет 500 мсек.

Посмотреть текущий интервал отправки можно методом [GetSettings](account/GetSettings.md), параметр `delaySendMessagesMilliseconds`.

## Изменение интервала отправки сообщений

Для изменения интервала отправки сообщений требуется выполнить запрос по адресу:

```
POST https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}
```

В теле запроса требуется указать только один параметр `delaySendMessagesMilliseconds`. 

### Пример тела запроса для установки интервала отправки 5 сек

```json
{
    "delaySendMessagesMilliseconds": 5000
}
```

### Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}"

payload = "{\r\n\t\"delaySendMessagesMilliseconds\": 5000\r\n}\r\n"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```