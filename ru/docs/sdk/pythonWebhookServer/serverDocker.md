# Пример разворачивания среды сервера в контейнере Docker

На машине должен быть установлен [docker](https://docs.docker.com/engine/install/).

Для получения образа из DockerHub воспользуемся командой:

```
sudo docker pull greenapi/whatsapp-api-webhook-server-python
```

Запустим образ в контейнере с указанием порта и отображением консоли:

```
sudo docker run --publish 8080:80 -it greenapi/whatsapp-api-webhook-server-python
```

Вместо порта 8080 можно указать любой свободный порт машины. В консоле [кабинета Green-Api](https://console.green-api.com/instanceList/) нужно будет указать IP (или внешнее имя машины) с указанием этого порта.

После запуска контейнера в консоль контейнера должны приходить вебхуки.