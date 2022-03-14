# Edengine

## Общие положения, описание архитектуры

Edengine - платформа для быстрого запуска образовательных программ в любой сфере (создание  и продажа онлайн-курсов)

Проект состоит из 2-х платформ, завязанных на backend сервис edengine_units_api
   * app.edengine.ru - плаформа для авторов, размещающих курсы
   * edstore.io  - маркетплейс: покупка курсов студентами
  - edengine_units_api - backend - сервис


![архитектура серверной инфраструктуры](edengine.jpg "архитектура серверной инфраструктуры")

Дополнительные ресурсы используемые в проекте:
  * postgresql - хранение данных (пароли, url`ы и т.д.)
  * s3 - хранение видеоконтента
  * redis - хранение токенов авторизации
  * nginx - веб-сервер
  * certbot - генерация ssl-сертификатов
  * python 3.8 - для работы backend - сервиса
  * npm - сборка фронта
  * git - получение кода из репозитория


## Установка и настройка серверов и сервисов проекта

### Установка балансера edengine-bal-01

  - Создаем новый сервер edengine-bal-01, выполняем базовую настройку ОС
  - устанавливаем системные зависимости: `sudo apt install nginx certbot` 
  - в /etc/nginx/conf.d/ создаем файл app.edengine.ru.conf (пример файла в nginx-files/app.edengine.ru.conf)
  - в /etc/nginx/conf.d/ создаем файл edstore.io.conf (пример файла в nginx-files/edstore.io.conf)

### Установка сервера баз данных edengine-db-01

- Создаем новый сервер edengine-db-01, выполняем базовую настройку ОС
- устанавливаем системные зависимости: `sudo apt install postgresql postgresql-contrib`
- в /etc/postgresql/12/main/pg_hba.conf прописываем директивы, разрешающие подключене с удаленных хостов по паролю:  
        `host    edengine_units_api_db all      'ip сервера приложений'           md5`  
        `host    edengine_units_api_db all      'ip балансира'           md5` (добавляем если есть необходимость доступа к БД из-вне через ssh-тоннель)  
 - создаем пользователя бд edengine_units_api_admin:
 - создаем бд edengine_units_api_admin:

