# Python WhatsApp Library

[![Python application](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-app.yml/badge.svg)](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-app.yml)
[![Upload Python Package](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-publish.yml/badge.svg)](https://github.com/green-api/whatsapp-api-client-python/actions/workflows/python-publish.yml)

[Python library](https://github.com/green-api/whatsapp-api-client-python) for integration with WhatsAPP messanger via API of [green-api.com](https://green-api.com/en) service. To use the library you have to get a registration token and an account id in the [personal area](https://console.green-api.com). There is a free developer account tariff plan.

#### API

You can find REST API documentation by [url](https://green-api.com/en/docs/api/). The library is a wrapper for REST API, so the documentation at the above url applies to the library as well.

#### Authorization

To send a message or to execute some other Green-API method, you have to have the WhatsApp account in the phone application to be authorized. To authorize your account please go to the [personal area](https://console.green-api.com) and scan a QR-code using the WhatsApp application.

#### [How to send a text message](sendmessage.md)
#### [How to send a file by URL](sendfilebyurl.md)
#### [How to send a file by uploading from the disk](sendfilebyupload.md)
#### [How to handle incoming notifications](startReceiveNotification.md)
#### [The full list of the library methods](fullmethods.md)

#### Service methods documentation

[Service methods documentation](https://green-api.com/docs/api/)

#### External products

- [requests](https://requests.readthedocs.io) - for http requests

#### Lisence

Licensed under MIT terms. Please see file [LICENSE](https://github.com/green-api/whatsapp-api-client-python/blob/master/LICENSE)
