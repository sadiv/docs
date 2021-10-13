# Chat and correspondent Id

В Green&nbsp;API supports two types of chats - [personal chat](#cus) and [group chat](#gus).
A personal chat is used to send personal messages to the recipient. Group chat is used to organize communication of several participants in a group. To work with group chats, the Green&nbsp;API provides relevant methods. 
Before sending a message to a personal or group chat, you need to get a chat Id. 

## Correspondent Id {#corr}
Correspondent Id is used to identify the recipient in outgoing messages and to identify the sender in incoming messages, as well as in any other API methods that require a correspondent to be identified. The format of the correspondent Id is the same as the [Personal chat](#cus) Id.

## Personal chat {#cus}
The format of the personal chat Id is formed according to the template `00000000000@c.us`, where  it is required to use the recipient's phone number instead of zeros`00000000000`. The telephone number must be entered in full, with the country code and without spaces. Example:

```
79001234567@c.us
```

## Group chat {#gus}
Group chat Id presents a string of `00000000000-XXXXXXXXXX@g.us` form. Example:

```
79001234567-1581234048@g.us
```

Group chat Id may be received by various Green&nbsp;API methods, for example:

- [Create group](groups/CreateGroup.md)
- [Get outgoing messages journal](journals/LastOutgoingMessages.md)
- [Get incoming messages journal](journals/LastIncomingMessages.md)
- [Incoming message: Text](receiving/notifications-format/incoming-message/TextMessage.md)
- etc.

> **Important**
>
> You are **NOT required** to generate Group chat Id manually. It is generated automatically by the system and returned by various Green&nbsp;API methods.
