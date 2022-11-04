# Пример подготовки среды сервера на операционной системе Windows

Для использования IIS (Internet Information Services) в качетсве веб-сервере требуется настроить конфигурационный файл web.config,
чтобы служба IIS могла правильно выполнять код Python. Этот файл располагается в папке публикации вашего веб-сервера.
Интерпритатор языка можно скачать с официального сайта [python.org](https://www.python.org/downloads/).

После установки интерпритатора следует указать обработчик HttpPlatform в файле web.config. Этот обработчик будет передавать подключения в автономный процесс Python.

Пример конфигурационного файла:

```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="<Path-to-python>\python.exe"
                  arguments="<Path-to-server-file>\echo.py
                  stdoutLogEnabled="true"
                  stdoutLogFile="<Path-to-log-file>\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SOME_VARIABLE" value="%SOME_VAR%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

"\<Path-to-python\>" - путь к исполняемому файлу интерпритатора Python

"\<Path-to-server-file\>" - путь к исполняемому файлу сервера (например echo.py из примера к библиотеке)

"\<Path-to-log-file\>" - путь к файл логов

Также потребуется открыть соответствующий порт во внешнюю сеть, установив настройка брандмауэра (Дополнительные параметры -> Правила для входящих подключений -> Создать правило -> Тип правила = Порт, Протоколы и порт -> TCP, указать порт, Действие -> Разрешить соединение)