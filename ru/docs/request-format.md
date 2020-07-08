# Выполнение запросов

Для выполнения запроса к Green API необходимо выполнить GET или POST запрос на адрес 

```
https://api.green-api.com/waInstance{{idInstance}}/{{method}}/{{apiTokenInstance}}
```

Адрес запроса формируется из номера аккаунта `idInstance` и ключа доступа `apiTokenInstance`, которые требуется предварительно получить в [Личном кабинете](https://cabinet.green-api.com) согласно разделу [Перед началом работы](before-start#parameters).

В качестве параметра `method` используется требуемый метод API, описанный в [Документации API](api/index.md).

Пример запроса для отправки сообщения методом [SendMessage](api/sending/SendMessage):
```
https://api.green-api.com/waInstance1234/SendMessage/bde035edae3fc00bc116bd112297908d8145e5ba8decc5d884
```

## Заголовки запроса
Большинство запросов должны содержать стандартные заголовки:

- `Content-Type` - `application/json`

В некоторых случаях заголовки могут отличаться, например, для метода отправки файла [SendFileByUpload](api/sending/SendFileByUpload) 

## Отладка запросов

Для отладки запросов к Green API рекомендуется использовать [Коллекцию Postman](postman-collection)
