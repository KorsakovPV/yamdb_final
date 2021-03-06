# yamdb_final

[![Yamdb-app workflow](https://github.com/KorsakovPV/yamdb_final/workflows/Yamdb-app_workflow/badge.svg)](https://github.com/KorsakovPV/yamdb_final/actions)

![YAMDB banner](https://github.com/KorsakovPV/yamdb_final/blob/master/static/logo.jpg)

 Основан на проекте api_yamdb (https://github.com/KorsakovPV/api_yamdb/) + CI/CD

# REST API для сервиса YaMDb — базы отзывов о фильмах, книгах и музыке. (Совместный проект студентов Яндекс.Практикум)

Проект YaMDb собирает отзывы (*Review*) пользователей на произведения (*Title*). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (*Category*) может быть расширен (например, можно добавить категорию *«Изобразительное искусство»* или *«Ювелирка»*).

Сами произведения в YaMDb не хранятся, **здесь нельзя посмотреть фильм или послушать музыку**.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха. Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

Благодарные или возмущённые читатели оставляют к произведениям текстовые отзывы (*Review*) и выставляют произведению рейтинг (оценку в диапазоне от одного до десяти). Из множества оценок автоматически высчитывается средняя оценка произведения.

## Подготовка к работе:

Клонируйте репозиторий на локальную машину.
```
git clone https://github.com/KorsakovPV/yamdb_final
```
В корневой папке находится файл .env.template, в котором описаны все нужные переменные и их примерные значения. По образу и подобию необходимо создать файл .env и заполнить его своими значениями.

Запустите процесс сборки и запуска контейнеров. Для запуска в фоновом режиме примените ключ -d
```
docker-compose up
```
Запустите терминал внутри контейнера (команду необходимо выполнить в папке с файлом docker-compose.yaml)
```
docker-compose exec web bash
```
Для того, чтобы "накатить" миграцию базы данных, выполните в терминале контейнера команду
```
python manage.py migrate
```
Для работы с админкой Django необходимо создать суперюзера
```
python manage.py createsuperuser
```
По желанию можно подгрузить в базу тестовые данные
```
python manage.py loaddata fixtures.json
```
Остановить работу и удалить контейнеры можно командой
```
docker-compose down
```

## Технологии
Код приложения написан на **[Python](https://www.python.org/)**. Применены фреймворки **[Django](https://www.djangoproject.com/)**, **[Django rest framework](https://www.django-rest-framework.org/)**. Для хранения применена база данных **[PostgreSQL](https://www.postgresql.org/)**.
Для сборки контейнеров и развертывания приложений применен **[Docker](https://www.docker.com/)** и **[Docker-Compose](https://docs.docker.com/compose/)**.

### Необходимые компоненты

Для развернывания приложения необходимо установить **[Docker](https://docs.docker.com/engine/install/)** и **[Docker-Compose](https://docs.docker.com/compose/install/)**

## Над проектом работали:
**[Павел Корсаков](https://github.com/KorsakovPV)**. Управление пользователями: система регистрации и аутентификации, права доступа, работа с токеном, система подтверждения e-mail, поля.

**[Владимир Самородов](https://github.com/Jejevkin)**.  Категории, жанры и произведения: модели, view и эндпойнты для них.

**[Олег Завитаев](https://github.com/TheZavitaev)**. Отзывы и комментарии: модели и view, эндпойнты, права доступа для запросов. Рейтинги произведений.

