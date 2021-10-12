# Messages sending delay

When sending messages or files, all data are put in the send queue. All messages are sent from the queue sequentially in the order they come in the [FIFO](https://ru.wikipedia.org/wiki/FIFO) queue. This sets the message sending delay from the queue. To change the messages sending delay, use [SetSettings](account/SetSettings.md) method and `delaySendMessagesMilliseconds` parameter. 

The minimum message sending delay is 500 msec.

To check the current sending delay, use [GetSettings](account/GetSettings.md) method, `delaySendMessagesMilliseconds` parameter.

## Messages sending delay change

To change messages sending delay, you have to execute a request at:

```
POST https://api.green-api.com/waInstance{{idInstance}}/SetSettings/{{apiTokenInstance}}
```

You have to specify the only parameter `delaySendMessagesMilliseconds` in the request body. 

### Request body example to set 5 second messages sending delay 

```json
{
    "delaySendMessagesMilliseconds": 5000
}
```

### Python request example  {#request-example-python}

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
