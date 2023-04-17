# Проект YaMDB


![Api Yamdb](https://github.com/aerobean/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Описание
Приложение для оценки различных произведений

Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий может быть расширен администратором.

Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.

Произведению может быть присвоен жанр из списка предустановленных. Новые жанры может создавать только администратор.

Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти; из пользовательских оценок формируется усреднённая оценка произведения — рейтинг. На одно произведение пользователь может оставить только один отзыв.

## Техническое описание проекта YaMDb

## Список используемых технологий:
- Python 3
- Django
- Django REST Framework
- Simple JWT
- Gunicorn

### Временный адрес сервера: 158.160.96.224

## Последовательность действий, необходимых для запуска проекта
1. Клонировать репозиторий и перейти в него в командной строке:
```
git clone git@github.com:LuckyPoRus/infra_sp2.git
```
2. Переход в директорию с проектом:
```
cd api_yamdb
```
3. Cоздать и активировать виртуальное окружение:
```
python -m venv venv
```
4. Активировать виртуальное окружение:
```
source venv/scripts/activate
```
5. Оновление PIP:
```
python -m pip install --upgrade pip
```
6. Установка зависимостей используемых в проекте:
```
pip install -r requirements.txt
```
7. Переходим в папку с файлом docker-compose.yaml:
```
cd infra
8. Создайте и разместите в директории /infra .env файл. Шаблон для заполнения .env-файла
```
DB_ENGINE=<...>
DB_NAME=<...>
POSTGRES_USER=<...>
POSTGRES_PASSWORD=<...>
DB_HOST=<...>
DB_PORT=<...>
SECRET_KEY=<...>
```
9. Соберите и запустите контейнер с помощью Docker-compose
```
docker-compose build
docker-compose up
```
10. Выполнить миграции через Docker-compose
```
docker-compose exec web python manage.py makemigrations --noinput  
docker-compose exec web python manage.py migrate --noinput
```
11. Собрать через Docker-compose статику
```
docker-compose exec web python manage.py collectstatic --no-input
```  
12. Создайте суперпользователя
```
docker-compose exec web python manage.py createsuperuser
```  
13. Заполните базу начальными данными. Скопируйте файл fixtures.json в контейнер web в папку "api_yambd" и выполните команду для заполнения БД
```
docker-compose exec web python manage.py loaddata infra_sp2/infra/fixtures.json
```
## Описание запросов API проекта доступно по адресу:
```
http://127.0.0.1:8000/redoc/

## Разработчик
- Максим Асташев (https://github.com/aerobean/)
