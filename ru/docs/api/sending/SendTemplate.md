# SendTemplate

Метод предназначен для отправки шаблонного сообщения из официального API. Удобен для массовых рассылок. Для отправки данного сообщения необходимо иметь или предварительно создать шаблон сообщения. Если у вас нет своего шаблона, то мы можем помочь, для этого свяжитесь с нами через почту support@green-api.com или другим удобным способом.

## Запрос {#request}

Для отправки сообщения со ссылкой требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/sendTemplate/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Да | [Идентификатор чата](../chat-id.md)
`namespace` | **string** | Да | имя пространства имен из официального АПИ
`namespace` | **string** | Да | имя шаблона сообщения
`languageCode` | **string** | Да | Код языка локализации шаблона сообщения
`params` | **array** | Нет | Массив параметров, используемых в шаблоне. Обязательный, если шаблон использует параметры
`quotedMessageId` | **string** | Нет | Идентификатор цитируемого сообщения,если указан то сообщение отправится с цитированием указанного сообщения чата

Поля массива `params`

Параметр | Тип | Описание
----- | ----- | -----
`default` | **string** | значение параметра default


### Пример тела запроса {#request-example-body}

Отправка сообщения в личный чат:
```json
{
    "chatId": "79001234567@c.us",
    "namespace": "not_existing_namespace",
    "name": "not_existing_template",
    "languageCode": "ru",
    "params": [
        {"default": "Dear customer"}
    ]
}

```
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | -----
`idMessage ` | **string** | Идентификатор отправленного сообщения 

### Пример тела ответа {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```

### Ошибки {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на curl  {#request-example-curl}

```
curl --location --request POST 'https://api.green-api.com/waInstance{{idInstance}}/sendTemplate/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "79001234567@c.us",
    "namespace": "not_existing_namespace",
    "name": "not_existing_template",
    "languageCode": "ru",
    "params": [
        {"default": "Dear customer"}
    ]
}
'
```
