### Kittygram
<img width="857" alt="image" src="https://github.com/evgeniazagorodnykh/kittygram_final/assets/129388336/95d7cabb-0823-430c-9880-61f2ce9d0ea7">


## Описание

Через Kittygram пользователи могут делиться своими котиками и добавлять к ним их фотографии. А также следить за новыми котами других пользователей.

## Как запустить проект на сервере:

Создайте на своем сервере в директорию kittygram/  и скопируйте файл docker-compose.production.yml. Сделать это можно, например, при помощи утилиты SCP:
```
scp -i path_to_SSH/SSH_name docker-compose.production.yml \
    username@server_ip:/home/username/taski/docker-compose.production.yml
```
Выполните эту команду на сервере в папке kittygram/:
```
sudo docker compose -f docker-compose.production.yml up -d
```
Выполните миграции, соберите статические файлы бэкенда и скопируйте их в /backend_static/static/:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/
```
Обновите конфиг Nginx и переагрузите его.
Откройте в браузере страницу проекта https://kittygram.serveblog.net/

## Примеры запросов:
```
/kittygram.serveblog.net/
/kittygram.serveblog.net/api/user/
/kittygram.serveblog.net/cats/add
```
