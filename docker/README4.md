# Домашнее задание к занятию "5.4. Практические навыки работы с Docker"

## Задача 1

В данном задании вы научитесь изменять существующие Dockerfile, адаптируя их под нужный инфраструктурный стек.

Измените базовый образ предложенного Dockerfile на Arch Linux c сохранением его функциональности.

```text
FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:vincent-c/ponysay && \
    apt-get update
 
RUN apt-get install -y ponysay

ENTRYPOINT ["/usr/bin/ponysay"]
CMD ["Hey, netology”]
```

Для получения зачета, вам необходимо предоставить:
- Написанный вами Dockerfile
  
```
FROM archlinux:base-20201220.0.11678

RUN pacman -Syu --noconfirm
RUN pacman -S ponysay --noconfirm

ENTRYPOINT ["/usr/bin/ponysay"]
CMD ["Hey, netology”]
```
- Скриншот вывода командной строки после запуска контейнера из вашего базового образа
  
Прикрепил к заданию

- Ссылку на образ в вашем хранилище docker-hub

https://hub.docker.com/r/enotys/pony

## Задача 2

В данной задаче вы составите несколько разных Dockerfile для проекта Jenkins, опубликуем образ в `dockerhub.io` и посмотрим логи этих контейнеров.

- Составьте 2 Dockerfile:

    - Общие моменты:
        - Образ должен запускать [Jenkins server](https://www.jenkins.io/download/)

    - Спецификация первого образа:
        - Базовый образ - [amazoncorreto](https://hub.docker.com/_/amazoncorretto)
        - Присвоить образу тэг `ver1`

```docker run -it --publish 8080:8080 ver1```
```
MacBook-Pro-enot:jenkins-amazon enot$ docker run -it --publish 8080:8080 ver1
Running from: /tmp/jenkins/jenkins.war
webroot: $user.home/.jenkins
2021-05-07 10:09:33.444+0000 [id=1]	INFO	org.eclipse.jetty.util.log.Log#initialized: Logging initialized @640ms to org.eclipse.jetty.util.log.JavaUtilLog
2021-05-07 10:09:33.631+0000 [id=1]	INFO	winstone.Logger#logInternal: Beginning extraction from war file
2021-05-07 10:09:35.271+0000 [id=1]	WARNING	o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
2021-05-07 10:09:35.370+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: jetty-9.4.39.v20210325; built: 2021-03-25T14:42:11.471Z; git: 9fc7ca5a922f2a37b84ec9dbc26a5168cee7e667; jvm 1.8.0_292-b10
2021-05-07 10:09:35.718+0000 [id=1]	INFO	o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
2021-05-07 10:09:35.783+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: DefaultSessionIdManager workerName=node0
2021-05-07 10:09:35.784+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: No SessionScavenger set, using defaults
2021-05-07 10:09:35.786+0000 [id=1]	INFO	o.e.j.server.session.HouseKeeper#startScavenging: node0 Scavenging every 600000ms
2021-05-07 10:09:36.272+0000 [id=1]	INFO	hudson.WebAppMain#contextInitialized: Jenkins home directory: /root/.jenkins found at: $user.home/.jenkins
2021-05-07 10:09:36.436+0000 [id=1]	INFO	o.e.j.s.handler.ContextHandler#doStart: Started w.@345e5a17{Jenkins v2.277.4,/,file:///root/.jenkins/war/,AVAILABLE}{/root/.jenkins/war}
2021-05-07 10:09:36.471+0000 [id=1]	INFO	o.e.j.server.AbstractConnector#doStart: Started ServerConnector@5c86a017{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
2021-05-07 10:09:36.471+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: Started @3668ms
2021-05-07 10:09:36.473+0000 [id=22]	INFO	winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
2021-05-07 10:09:38.100+0000 [id=29]	INFO	jenkins.InitReactorRunner$1#onAttained: Started initialization
2021-05-07 10:09:38.135+0000 [id=27]	INFO	jenkins.InitReactorRunner$1#onAttained: Listed all plugins
2021-05-07 10:09:39.472+0000 [id=27]	INFO	jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
2021-05-07 10:09:39.484+0000 [id=34]	INFO	jenkins.InitReactorRunner$1#onAttained: Started all plugins
2021-05-07 10:09:39.509+0000 [id=31]	INFO	jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
2021-05-07 10:09:40.092+0000 [id=27]	INFO	jenkins.InitReactorRunner$1#onAttained: System config loaded
2021-05-07 10:09:40.092+0000 [id=28]	INFO	jenkins.InitReactorRunner$1#onAttained: System config adapted
2021-05-07 10:09:40.093+0000 [id=28]	INFO	jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
2021-05-07 10:09:40.095+0000 [id=29]	INFO	jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
2021-05-07 10:09:40.115+0000 [id=47]	INFO	hudson.model.AsyncPeriodicWork#lambda$doRun$0: Started Download metadata
2021-05-07 10:09:40.135+0000 [id=47]	INFO	hudson.util.Retrier#start: Attempt #1 to do the action check updates server
2021-05-07 10:09:40.508+0000 [id=29]	INFO	jenkins.install.SetupWizard#init:

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

2f41f811ae5349cbac3727edde938428

This may also be found at: /root/.jenkins/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

2021-05-07 10:09:50.845+0000 [id=29]	INFO	jenkins.InitReactorRunner$1#onAttained: Completed initialization
2021-05-07 10:09:50.871+0000 [id=21]	INFO	hudson.WebAppMain$3#run: Jenkins is fully up and running
2021-05-07 10:09:51.243+0000 [id=47]	INFO	h.m.DownloadService$Downloadable#load: Obtained the updated data file for hudson.tasks.Maven.MavenInstaller
2021-05-07 10:09:51.244+0000 [id=47]	INFO	hudson.util.Retrier#start: Performed the action check updates server successfully at the attempt #1
2021-05-07 10:09:51.248+0000 [id=47]	INFO	hudson.model.AsyncPeriodicWork#lambda$doRun$0: Finished Download metadata. 11,125 ms

```

```
FROM amazoncorretto:latest

COPY ./jenkins.war /tmp/jenkins/jenkins.war
COPY ./jenkins.sh /tmp/jenkins/jenkins.sh

WORKDIR /tmp/jenkins/

EXPOSE 8080

ENTRYPOINT ["/tmp/jenkins/jenkins.sh"]
```

https://hub.docker.com/repository/docker/enotys/ver1

- Спецификация второго образа:
        - Базовый образ - [ubuntu:latest](https://hub.docker.com/_/ubuntu)
        - Присвоить образу тэг `ver2`
  
Этот запускал на 9090 порту ради эксперимента

```
FROM ubuntu:latest

RUN apt-get update && apt-get install -y openjdk-8-jre

COPY ./jenkins.war /tmp/jenkins/jenkins.war
COPY ./jenkins.sh /tmp/jenkins/jenkins.sh

WORKDIR /tmp/jenkins/

EXPOSE 9090

ENTRYPOINT ["/tmp/jenkins/jenkins.sh"]

```

```
MacBook-Pro-enot:jenkins-amazon enot$ docker run -it --publish 9090:9090 ver2
Running from: /tmp/jenkins/jenkins.war
webroot: $user.home/.jenkins
2021-05-07 10:38:33.912+0000 [id=1]	INFO	org.eclipse.jetty.util.log.Log#initialized: Logging initialized @621ms to org.eclipse.jetty.util.log.JavaUtilLog
2021-05-07 10:38:34.133+0000 [id=1]	INFO	winstone.Logger#logInternal: Beginning extraction from war file
2021-05-07 10:38:35.346+0000 [id=1]	WARNING	o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
2021-05-07 10:38:35.438+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: jetty-9.4.39.v20210325; built: 2021-03-25T14:42:11.471Z; git: 9fc7ca5a922f2a37b84ec9dbc26a5168cee7e667; jvm 1.8.0_292-8u292-b10-0ubuntu1~20.04-b10
2021-05-07 10:38:35.739+0000 [id=1]	INFO	o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
2021-05-07 10:38:35.800+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: DefaultSessionIdManager workerName=node0
2021-05-07 10:38:35.801+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: No SessionScavenger set, using defaults
2021-05-07 10:38:35.803+0000 [id=1]	INFO	o.e.j.server.session.HouseKeeper#startScavenging: node0 Scavenging every 660000ms
2021-05-07 10:38:36.263+0000 [id=1]	INFO	hudson.WebAppMain#contextInitialized: Jenkins home directory: /root/.jenkins found at: $user.home/.jenkins
2021-05-07 10:38:36.408+0000 [id=1]	INFO	o.e.j.s.handler.ContextHandler#doStart: Started w.@6cc0bcf6{Jenkins v2.277.4,/,file:///root/.jenkins/war/,AVAILABLE}{/root/.jenkins/war}
2021-05-07 10:38:36.446+0000 [id=1]	INFO	o.e.j.server.AbstractConnector#doStart: Started ServerConnector@465232e9{HTTP/1.1, (http/1.1)}{0.0.0.0:9090}
2021-05-07 10:38:36.446+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: Started @3156ms
2021-05-07 10:38:36.449+0000 [id=22]	INFO	winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
2021-05-07 10:38:38.083+0000 [id=29]	INFO	jenkins.InitReactorRunner$1#onAttained: Started initialization
2021-05-07 10:38:38.115+0000 [id=33]	INFO	jenkins.InitReactorRunner$1#onAttained: Listed all plugins
2021-05-07 10:38:39.617+0000 [id=28]	INFO	jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
2021-05-07 10:38:39.624+0000 [id=28]	INFO	jenkins.InitReactorRunner$1#onAttained: Started all plugins
2021-05-07 10:38:39.650+0000 [id=34]	INFO	jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
2021-05-07 10:38:40.281+0000 [id=27]	INFO	jenkins.InitReactorRunner$1#onAttained: System config loaded
2021-05-07 10:38:40.282+0000 [id=27]	INFO	jenkins.InitReactorRunner$1#onAttained: System config adapted
2021-05-07 10:38:40.282+0000 [id=27]	INFO	jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
2021-05-07 10:38:40.285+0000 [id=30]	INFO	jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
2021-05-07 10:38:40.311+0000 [id=47]	INFO	hudson.model.AsyncPeriodicWork#lambda$doRun$0: Started Download metadata
2021-05-07 10:38:40.342+0000 [id=47]	INFO	hudson.util.Retrier#start: Attempt #1 to do the action check updates server
2021-05-07 10:38:40.670+0000 [id=29]	INFO	jenkins.install.SetupWizard#init:

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

66390d1c88214785904e55907588c3e7

This may also be found at: /root/.jenkins/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

2021-05-07 10:38:52.515+0000 [id=29]	INFO	jenkins.InitReactorRunner$1#onAttained: Completed initialization
2021-05-07 10:38:52.532+0000 [id=21]	INFO	hudson.WebAppMain$3#run: Jenkins is fully up and running
2021-05-07 10:38:53.003+0000 [id=47]	INFO	h.m.DownloadService$Downloadable#load: Obtained the updated data file for hudson.tasks.Maven.MavenInstaller
2021-05-07 10:38:53.005+0000 [id=47]	INFO	hudson.util.Retrier#start: Performed the action check updates server successfully at the attempt #1
2021-05-07 10:38:53.009+0000 [id=47]	INFO	hudson.model.AsyncPeriodicWork#lambda$doRun$0: Finished Download metadata. 12,695 ms

```

```
jenkins.sh

#!/bin/bash -e

exec java -jar /tmp/jenkins/jenkins.war --httpPort=9090 "$@"


```

https://hub.docker.com/repository/docker/enotys/ver2

- Соберите 2 образа по полученным Dockerfile
- Запустите и проверьте их работоспособность
- Опубликуйте образы в своём dockerhub.io хранилище

Для получения зачета, вам необходимо предоставить:
- Наполнения 2х Dockerfile из задания
- Скриншоты логов запущенных вами контейнеров (из командной строки)
- Скриншоты веб-интерфейса Jenkins запущенных вами контейнеров (достаточно 1 скриншота на контейнер)
- Ссылки на образы в вашем хранилище docker-hub

## Задача 3

В данном задании вы научитесь:
- объединять контейнеры в единую сеть
- исполнять команды "изнутри" контейнера

Для выполнения задания вам нужно:
- Написать Dockerfile:
    - Использовать образ https://hub.docker.com/_/node как базовый
    - Установить необходимые зависимые библиотеки для запуска npm приложения https://github.com/simplicitesoftware/nodejs-demo
    - Выставить у приложения (и контейнера) порт 3000 для прослушки входящих запросов
    - Соберите образ и запустите контейнер в фоновом режиме с публикацией порта
    
Сделал так:

```
FROM node

COPY ./nodejs-demo ./nodejs-demo

WORKDIR /nodejs-demo

RUN npm install

EXPOSE 3000 80 443

ENV SIMPLICITE_URL=http://0.0.0.0:3000

ENTRYPOINT ["npm"]
CMD ["start"]
```

Без `ENV SIMPLICITE_URL=http://0.0.0.0:3000` он стартует на localhost:3000

Создал сеть через `docker network create node-demo-network`
```
MacBook-Pro-enot:network-hw enot$ docker network ls
NETWORK ID     NAME                DRIVER    SCOPE
a5317c2575db   adp                 bridge    local
037dacda7b95   bridge              bridge    local
109a9d02f13a   host                host      local
f7a4c40f44e8   node-demo-network   bridge    local
9a7e0ca62842   none                null      local
```
Запустил контейнер вот так:
`docker run -it -p 3000:3000 --network=node-demo-network nodejs-demo`

- Запустить второй контейнер из образа ubuntu:latest
- Создайть `docker network` и добавьте в нее оба запущенных контейнера

Второй:

```
FROM ubuntu:latest

RUN apt-get update && apt-get install -y curl

EXPOSE 8080 3000

ENTRYPOINT ["/bin/bash"]
```
Запустил так же как демон:

`run -itd --network=node-demo-network node-ubuntu`

Оба как видно в одной сети:

```
MacBook-Pro-enot:node enot$ docker network inspect node-demo-network
[
    {
        "Name": "node-demo-network",
        "Id": "f7a4c40f44e8bb5fdce7f7f9222e529c83d6198d66291537b9dee97ae4222426",
        "Created": "2021-05-07T12:19:46.7122689Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "54a4ff8346b13eb5e9a958a14812a8afd29c48fba71498d077afd0a7fe465c7d": {
                "Name": "optimistic_heisenberg",
                "EndpointID": "fa930afc7a73bf98e295d2591b34bf91048f43691394185f3d70d2794b060e58",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            },
            "8dc5c1ac462c0d1d3d353f1ec2fa6e2fbe6ab15380ba5716b47f74733fe924ee": {
                "Name": "hopeful_ramanujan",
                "EndpointID": "0e30d4be690e80db3469561316254c063c825c911143b841fb73437bcf729459",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
```

- Используя `docker exec` запустить командную строку контейнера `ubuntu` в интерактивном режиме
  
``
docker exec -it 54a4ff8346b1 bash
``
и из контейнера пробовал:
```
curl 0.0.0.0:3000/
и
curl localhost:3000/
и
curl -X GET http://172.18.0.3:3000/
curl: (7) Failed to connect to 172.18.0.3 port 3000: Connection refused
и
curl -X GET 'nodejs-demo'
и 
```

Но всегда `Connection refused :(`

- Используя утилиту `curl` вызвать путь `/` контейнера с npm приложением

Для получения зачета, вам необходимо предоставить:
- Наполнение Dockerfile с npm приложением
- Скриншот вывода вызова команды списка docker сетей (docker network cli)
- Скриншот вызова утилиты curl с успешным ответом

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
