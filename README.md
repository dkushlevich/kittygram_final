<div align=center>
  
  # CI/CD для проекта [Kittygram](https://kittygramhostname.ddns.net/)
  
  [![CICD-Kittygram](https://github.com/dkushlevich/kittygram_final/workflows/CICD-Kittygram/badge.svg)](https://github.com/dkushlevich/kittygram_final/workflows/CICD-Kittygram/badge.svg)
  
  ![Python](https://img.shields.io/badge/Python-3.9.10-blue)
  ![Django](https://img.shields.io/badge/Django-3.2.16-blue)
  ![Django_REST_framework](https://img.shields.io/badge/Django_REST_framework-3.12.4-blue)
  ![Nginx](https://img.shields.io/badge/Nginx-1.18.0-blue)
  ![Gunicorn](https://img.shields.io/badge/Gunicorn-20.1.0-blue)

</div>

CI/CD API сервиса Kittygram.Workflow включает в себя последовательность автоматических действий, таких как запуск тестов, обновление образа проекта на DockerHub, автоматический деплой на боевой сервер и запуск сервиса. Кроме того, при выполнении команды push, происходит отправка уведомления в Телеграм о успешном завершении workflow.

## Проект Kittygram




Kittygram - SPA, предназначенное для всех, кто увлекается котиками и хочет делиться фотографиями и достижениями своих питомцев с другими пользователями.

В Kittygram предоставлены интерфейсы для регистрации новых и для аутентификации зарегистрированных пользователей.

Аутентифицированным пользователям проект позволяет добавлять новых питомцев на сайт.

Для каждого нового котика нужно указать его имя, год рождения и достижения(выбрать из уже существующих или создать новое), выбрать цвет . Опционально можно загрузить фотографию своего питомца; для котиков без фотографии будет выводиться изображение по умолчанию. Информацию о собственных котах можно изменить или вовсе удалить с сайта.

На одной странице отображается не более десяти котиков.

Все вышеперечисленные возможности работают на базе API


## Ресурсы API Kittygram

* Ресурс **cats**: котики
* Ресурс **achivements**: достижения котиков
* Ресурс **users**: пользователи
* Ресурс **token**: создание токена

## Описание работы Workflow проекта

- **запускается при выполнении команды git push**
- **tests:** проверка кода на соответствие PEP8, запуск pytest.
- **build_and_push_to_docker_hub:** сборка и размещение образа проекта на DockerHub.
- **deploy:** автоматический деплой на боевой сервер и запуск проекта.
- **send_massage:** отправка уведомления пользователю в Телеграм.

## Архитектура проекта в контейнерах

<div align=center>
  <img src="https://pictures.s3.yandex.net/resources/sprint2_picture10_1684346618.png" alt="Danila Kushleich" height="400">
</div>


## Подготовка сервера к деплою проекта

1. Создать директорию kittygram/ в домашней директории сервера.

2. Установить Nginx и настроить конфигурацию так, чтобы все запосы шли в докер на порт 9000.
    
    ```bash
        sudo apt install nginx -y 
        sudo nano etc/nginx/sites-enabled/default
    ```
    
    Конфигурация nginx
    ```
        server {
            server_name 84.201.178.160 kittygramhostname.ddns.net;
            server_tokens off;
            client_max_body_size 20M;
        
            location / {
                proxy_set_header Host $http_host;
                proxy_pass http://127.0.0.1:9000;
        }
    ```
    
    > При необходимости настройте SSL-соединение

3. Установить docker-compose
   
``` bash
    sudo apt update
    sudo apt install curl
    curl -fSL https://get.docker.com -o get-docker.sh
    sudo sh ./get-docker.sh
    sudo apt-get install docker-compose-plugin     
```

4. Добавить в Secrets GitHub Actions данного репозитория на GitHub переменные окружения

``` bash
    DOCKER_USERNAME=<имя пользователя DockerHub>
    DOCKER_PASSWORD=<пароль от DockerHub>
    
    USER=<username для подключения к удаленному серверу>
    HOST=<ip сервера>
    PASSPHRASE=<пароль для сервера, если он установлен>
    SSH_KEY=<ваш приватный SSH-ключ>
    
    TELEGRAM_TO=<id вашего Телеграм-аккаунта>
    TELEGRAM_TOKEN=<токен вашего бота>
```



<div align=center>

## Контакты

[![Telegram Badge](https://img.shields.io/badge/-dkushlevich-blue?style=social&logo=telegram&link=https://t.me/dkushlevich)](https://t.me/dkushlevich) [![Gmail Badge](https://img.shields.io/badge/-dkushlevich@gmail.com-c14438?style=flat&logo=Gmail&logoColor=white&link=mailto:dkushlevich@gmail.com)](mailto:dkushlevich@gmail.com)

</div>
