# Сборщик логов

Скрипт читает `/var/log/syslog`, отбирает строки со словами `error`/`fail` и записывает их в `report.txt`.

## Контейнеризация

- `Dockerfile` — образ на базе `ubuntu:22.04` с Python HTTP-сервером на порту 8080.
- Запуск: `docker run -d -p 8080:8080 --name my-app -v /var/log:/var/log:ro my-script`
- Результат доступен по HTTPS через Nginx (reverse proxy) по адресу `https://<host>/report.txt`.
