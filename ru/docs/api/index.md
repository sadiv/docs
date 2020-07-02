# Документация API

Green API предоставляет HTTP API WhatsApp для отправки и получения сообщений, файлов, работы с групповыми чатами, получения списка контактов и других методов.

Перед началом работы с Green API требуется получить параметры доступа к аккаунту в [Личном кабинете](https://cabinet.green-api.com)

> Отправка и получение сообщений выполняется с вашего мобильного телефона. Поэтому телефон должен быть всегда заряжен и подключен к сети Интернет. Подключение мобильного телефона выполняется в [Личном кабинете](https://cabinet.green-api.com) путем считывания QR-кода из приложения [WhatsApp Business](https://www.whatsapp.com/business/)
>
>
> Рекомендуется использовать официальное мобильное приложение [WhatsApp Business](https://www.whatsapp.com/business/). Допускается также использование обычного мобильного приложения [WhatsApp](https://www.whatsapp.com/), если использование [WhatsApp Business](https://www.whatsapp.com/business/) по каким-либо причинам невозможно.

## Выполнение запроса

Для выполнения запроса к Green API необходимо выполнить GET или POST запрос на адрес `https://api.green-api.com/waInstance{{idInstance}}/{{apiTokenInstance}}`

Адрес запроса формируется из номера аккаунта `idInstance` и ключа доступа `apiTokenInstance`, которые требуется предварительно получить в [Личном кабинете](https://cabinet.green-api.com).

Пример адреса запроса:
```
https://api.green-api.com/waInstance1234/bde035edae3fc00bc116bd112297908d8145e5ba8decc5d884
```

## Отладка запросов

Для отладки запросов к Green API рекомендуется использовать [Green API - Postman Collection](https://github.com/green-api/green-api-postman-collection) 



