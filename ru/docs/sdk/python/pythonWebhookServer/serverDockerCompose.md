# Пример разворачивания сервера через Docker Compose

На машине должен быть установлен [Docker](https://docs.docker.com/engine/install/).
А также плагин [Docker compose](https://docs.docker.com/compose/install/)

Нужно скачать файл [docker-compose.yml](https://github.com/green-api/whatsapp-api-webhook-server-python/blob/master/docker-compose.yml). Например, с помощью команды wget (Linux):

```
wget https://raw.githubusercontent.com/green-api/whatsapp-api-webhook-server-python/master/docker-compose.yml
```

Затем собрать сервис из образа:

```
docker-compose build
```

И запустить его:

```
docker-compose up
```

Команды следует выполнять из каталога с файлом docker-compose.yml