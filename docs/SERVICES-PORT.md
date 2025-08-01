# Документация по Портам и Сетевым Настройкам Сервисов

## Сервисы приложения

| Название            | Назначение                | Протокол | Внешний порт | Внутренний порт | Сеть    |
|---------------------|---------------------------|----------|--------------|-----------------|---------|
| aniutils-frontend   | Веб-интерфейс             | HTTPs    | 3000         | 3000            | junketsu|
| aniutils-iam        | Сервис аутентификации     | HTTP     | —            | 5000            | junketsu|
| aniutils-huyak      | Управление пользователями | HTTP     | —            | 5001            | junketsu|
| aniutils-shiki      | API-сервис Shikimori      | HTTP     | —            | 5100            | junketsu|
| aniutils-mal        | API-сервис MyAnimeList    | HTTP     | —            | 5101            | junketsu|
| aniutils-anilist    | API-сервис Anilist        | HTTP     | —            | 5102            | junketsu|
| aniutils-re         | API-сервис Remanga        | HTTP     | —            | 5103            | junketsu|
| aniutils-re-jobs    | Фоновые процессы Remanga  | HTTP     | —            | 5150            | junketsu|
| aniutils-syncer     | Синхронизация списков     | HTTP     | —            | 5200            | junketsu|

---

## Базы данных

| Название            | Назначение                                   | БД         | Внешний порт | Внутренний порт | Сеть    |
|---------------------|----------------------------------------------|------------|--------------|-----------------|---------|
| mongo-titles        | База с нашей коллекцией аниме                | Mongo:6    | -            | 27017           | junketsu|
| postgres-user       | База с данными пользователей                 | Postgres:15| —            | 5432            | junketsu|
| redis-tokens        | База с токенами юзеров для внешней интеграции| Redis:7    | —            | 6379            | junketsu|
| redis-remanga-job   | База для фоновых работ реманги               | Redis:7    | —            | 6380            | junketsu|


## Правила

- Все внутренние сервисы доступны только внутри сети `docker`.
- Внешние сервисы (например, frontend) проброшены наружу через reverse proxy или ingress.
- Доступ к базе данных и Redis должен быть ограничен только сервисами приложения.

---

## Примечания

Для каждого нового сервиса необходимо:

- Назначить внутренний порт

- Указать, требуется ли проброс наружу

- Используйте .env файлы для конфигурации портов и тд
