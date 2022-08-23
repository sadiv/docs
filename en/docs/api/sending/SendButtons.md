# SendButtons

The method is aimed for sending a button message to a personal or a group chat. 
The message will be added to the send queue. Checking whatsapp authorization on the phone (i.e. availability in linked devices) is not performed. The message will be kept for 24 hours in the queue and will be sent immediately after phone authorization. 
The rate at which messages are sent from the queue is managed by [Message sending delay](../send-messages-delay.md) parameter.

## Request {#request}

To send a message, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendMessage/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`message` | **string** | Yes | Message text. Emoji 😃 characters supported
`footer` | **string** | No | Message footer. Useful for visually highlighting text related to buttons.
`buttons` | **array** | Yes | Message buttons
`quotedMessageId` | **string** | No | Quoted message ID. If present, the message will be sent quoting the specified chat message
`archiveChat` | **boolean** | No | Archives the chat to which the message was sent. Takes value: true.

`buttons` array parameters

Parameter | Type | Description
----- | ----- | -----
`buttonId` | **integer** | Button Id
`buttonText` | **string** | Button text


> The maximum length of a text message is 4096 characters

### Request body example {#request-example-body}

Sending a message to a personal chat:
```json
{
    "chatId": "79001234567@c.us",
    "message": "Hello",
    "footer": "Please choose the color:",
    "buttons": [
        {
            "buttonId": "1",
            "buttonText": "green"
        },
        {
            "buttonId": "2",
            "buttonText": "red"
        },
        {
            "buttonId": "3",
            "buttonText": "blue"
        }
    ]
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | -----
`idMessage ` | **string** | Sent message Id 

### Response body example {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### SendMessage errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## curl example

```
curl --location --request POST 'https://api.green-api.com/waInstance{{idInstance}}/sendMessage/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "79001234567@c.us",
	"message": "Please choose the color:",
    "buttons": [{"buttonId": "1", "buttonText": "green"}, {"buttonId": "2", "buttonText": "red"}, {"buttonId": "3", "buttonText": "blue"}]
}'
```
