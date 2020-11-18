# Домашнее задание
разворачиваем сетевую лабораторию

# otus-linux
Vagrantfile - для стенда урока 9 - Network

# Дано
https://github.com/erlong15/otus-linux/tree/network
(ветка network)

Vagrantfile с начальным построением сети
- inetRouter
- centralRouter
- centralServer

тестировалось на virtualbox

# Планируемая архитектура
построить следующую архитектуру

Сеть office1
- 192.168.2.0/26 - dev
- 192.168.2.64/26 - test servers
- 192.168.2.128/26 - managers
- 192.168.2.192/26 - office hardware

Сеть office2
- 192.168.1.0/25 - dev
- 192.168.1.128/26 - test servers
- 192.168.1.192/26 - office hardware


Сеть central
- 192.168.0.0/28 - directors
- 192.168.0.32/28 - office hardware
- 192.168.0.64/26 - wifi

```
Office1 ---\
-----> Central --IRouter --> internet
Office2----/
```
Итого должны получится следующие сервера
- inetRouter
- centralRouter
- office1Router
- office2Router
- centralServer
- office1Server
- office2Server

# Практическая часть
- Соединить офисы в сеть согласно схеме и настроить роутинг
- Все сервера и роутеры должны ходить в инет черз inetRouter
- Все сервера должны видеть друг друга
- у всех новых серверов отключить дефолт на нат (eth0), который вагрант поднимает для связи
- при нехватке сетевых интервейсов добавить по несколько адресов на интерфейс

# Теоретическая часть
- Найти свободные подсети

192.168.2.0 - нет свободных подсетей. Подсеть 192.168.2.0/24 разбита на 4 подеси /26.

192.168.1.0 - нет свободный подсетей. Подсеть 192.168.1.0/24 разбита на 1 подсеть /25 и две /26

192.168.0.0 - есть свободные подсети. Подсети 192.168.0.0/28 и 192.168.0.32/28 в подсети 192.168.0.0/26. Можно добавить 192.168.0.16/28 и 192.168.0.48/28.

Также можно добавить еще 3 подсети 192.168.0.0/26.

- Посчитать сколько узлов в каждой подсети, включая свободные

 192.168.2.0/26 - (2 в шестой степени)-2=62
 
 192.168.2.64/26 - 62
 
 192.168.2.128/26 - 62
 
 192.168.2.192/26 - 62
 
 192.168.1.0/25 - 126
 
 192.168.1.128/26 - 62
 
 192.168.1.192/26 - 62
 
 192.168.0.0/28 - 14
 
 192.168.0.32/28 - 14
 
 192.168.0.64/26 - 62
 
- Указать broadcast адрес для каждой подсети

 192.168.2.0/26 - 192.168.0.63
 
 192.168.2.64/26 - 192.168.0.127
 
 192.168.2.128/26 - 192.168.0.191
 
 192.168.2.192/26 - 192.168.0.255
 
 192.168.1.0/25 - 192.168.0.127
 
 192.168.1.128/26 - 192.168.0.191
 
 192.168.1.192/26 - 192.168.0.255
 
 192.168.0.0/28 - 192.168.0.31
 
 192.168.0.32/28 - 192.168.0.63
 
 192.168.0.64/26 - 192.168.0.127
 
- проверить нет ли ошибок при разбиении

нет

