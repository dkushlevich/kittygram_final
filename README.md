<div align=center>
  
# [Kittygram](https://kittygramhostname.ddns.net/)

![Github actions](https://github.com/dkushlevich/kittygram_final/actions/workflows/main.yml/badge.svg)

![Python](https://img.shields.io/badge/Python-3.9.10-blue)
![Django](https://img.shields.io/badge/Django-3.2.16-blue)
![Django_REST_framework](https://img.shields.io/badge/Django_REST_framework-3.12.4-blue)
![Nginx](https://img.shields.io/badge/Nginx-1.18.0-blue)
![Gunicorn](https://img.shields.io/badge/Gunicorn-20.1.0-blue)

</div>




Kittygram - SPA, предназначенное для всех, кто увлекается котиками и хочет делиться фотографиями и достижениями своих питомцев с другими пользователями.

В Kittygram предоставлены интерфейсы для регистрации новых и для аутентификации зарегистрированных пользователей.

Аутентифицированным пользователям проект позволяет добавлять новых питомцев на сайт.

Для каждого нового котика нужно указать его имя, год рождения и достижения(выбрать из уже существующих или создать новое), выбрать цвет . Опционально можно загрузить фотографию своего питомца; для котиков без фотографии будет выводиться изображение по умолчанию. Информацию о собственных котах можно изменить или вовсе удалить с сайта.

На одной странице отображается не более десяти котиков.

Все вышеперечисленные возможности работают на базе API


## Ресурсы API

* Ресурс **cats**: котики
* Ресурс **achivements**: достижения котиков
* Ресурс **users**: пользователи
* Ресурс **token**: создание токена



