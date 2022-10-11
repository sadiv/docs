# Common errors

## HTTP Ошибки

HTTP code | Error ID | Description
----- | ----- | -----
400 | `instance in starting process try later` | The account is in starting/restarting process. Please try again in a few seconds.
400 | `instance account not authorized` | The account is not authorized. To authorize your account, go to [My Profile](https://console.green-api.com) and scan the QR code from the [WhatsApp Business](https://www.whatsapp.com/business/) application on your phone.
400 | `bad request data` | The request data are not valid. Correct the error in the request parameters and try again.
466 | `correspondentsStatus` | The limit is used up, more details in the error body.
500 | `"File from url exceeded max upload size. Size: XXXXmb Limit: 100mb Url:` | An attempt to send a file larger than 100 MB

## Errors in the webhooks body

Error code | Parameter | Description | Solution
----- | ----- | ----- | -----
{{SWE001}}| `textMessage` | Error of receiving the first incoming message in the chat when sent to additional devices from the WhatsApp side. It is also observed in the native web and desktop versions. In fact, all additional devices get an empty message. | To capture th etext-marker {{SWE001}} in the message body and configure the bot to re-request the message from the sender with the following text:"Please send your message again, I couldn't see your reply".
{{SWE002}}| `downloadUrl` | Error of getting a large file over 100 MB. | To capture the text-marker {{SWE002}} in the message body and check the message in the phone.
{{SWE003}}| `textMessage` | Error of decrypting messages caused by the loss of the authorization keys relevance. | To capture the text-marker {{SWE003}}. When such messages come, it is necessary to delete all authorizations in the phone and scan the QR code again.
