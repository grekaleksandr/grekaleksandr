# Запуск splitter в docker

### Установка докера
Для того чтобы была возможность собрать контейнеры необходимо установить следующие пакеты: `docker` и `docker-compose`, а так же после установки запустить докер сервис.<br>
Для каждого дистрибутива установка и запуск сервисов происходит по разному, читайте документацию.<br>

### Установка проекта
```
Инициализацию проекта и управление контейнерами лучше делать от своего домашнего пользователя, чтобы не было в дальнейшем проблем с правами.
Для того чтобы была возможность работы с докером из под своего пользователя, нужно добаить его в группу "docker" (в некоторых дистрибутивах она может называться по другому)
```

Сборка контейнеров и первоначальная настройка проекта происходит через запуск скрипта `install.sh` в корне проекта.<br>
На этапе редактирования файла .env нужно настроить минимум `PHP_COMPOSER_AUTH_KEY` `WWW_PATH` и `SSH_KEYS_PATH`. Описание этих параметров читаем в самом файле .env.<br>
**Установка производится только в пустую директорию указанную в параметре `WWW_PATH`**<br>
Для повторного запуска скрипта инсталяции необходимо удалить файл `.env` в корне проекта и почистить `WWW_PATH` директорию.

### Запуск/Остановка контейнеров
Запуск контейнеров происходит через скрипт `docker.sh` в корне проекта.<br>
Какие есть параметры запуска и остановки можно почитать запустив `docker.sh -h` или `docker.sh --help`

## traefik
Для авторизации используются следующие данные
```
Логин: admin
Пароль: admintraefikroot
```

### Настройка hosts для traefik
```
130.10.0.1      splitter.docker api.splitter.docker cdn.splitter.docker supervisor.splitter.docker fpm.splitter.docker web.rabbitmq.splitter.docker api.rabbitmq.splitter.docker server.mysql.splitter.docker server.postgresql.splitter.docker server.redis.splitter.docker server.mongodb.splitter.docker
130.10.0.1      traefik.splitter.docker portainer.splitter.docker redis-commander.splitter.docker pgadmin4.splitter.docker phpmyadmin.splitter.docker
130.10.0.1      adwsys.rozetka.com.ua test.splitter.docker
```

### Домены traefik
```
splitter.docker - админка сплитера (порты 80 и 443)
api.splitter.docker - api splitter (порты 80 и 443)
cdn.splitter.docker - cdn splitter(еще не настроен) (порты 80 и 443)
traefik.splitter.docker - traefik если включен (порты 80 и 443)
supervisor.splitter.docker - supervisor (порт 9001)
fpm.splitter.docker - php-fpm  (порт 9000)
web.rabbitmq.splitter.docker - rabbitmq web interface (порт 15672)
api.rabbitmq.splitter.docker - rabbitmq api (порт 5672)
server.mysql.splitter.docker - mysql (порт 3306)
server.postgresql.splitter.docker  - postgresql (порт 5432)
server.redis.splitter.docker - redis (порт 6379)
server.mongodb.splitter.docker - mongodb (порт 27017)
portainer.splitter.docker - portainer если включен (порт 9000)
redis-commander.splitter.docker -  redis-commander если включен (порт 8081)
pgadmin4.splitter.docker - pgadmin4 если включен (порт 80)
phpmyadmin.splitter.docker - phpmyadmin если включен (порт 80)
```

### FAQ

[Часто задаваемые вопросы и ответы на них](docs/faq.md)# grekaleksandr
