## Описание проекта

«Фудграм» — сайт, где пользователи публикуют свои рецепты, добавляют чужие рецепты в избранное и подписываются на других авторов. Зарегистрированные пользователи могут пользоваться сервисом «Список покупок», который помогает составить список продуктов для приготовления выбранных блюд.

## Запуск backend

- Клонируйте репозиторий с проектом на свой компьютер.
- 
```bash
git clone https://github.com/UnDKab/Foodgram_final.git
cd foodgram-st/backend
```

- Установите и активируйте виртуальное окружение

```bash
python -m venv env
source ./env/bin/activate
```

- Установите зависимости из файла `requirements.txt`
```bash
pip install -r requirements.txt
```

### Выполните миграции:

```bash
python manage.py migrate
```
- Создайте superuser:

```bash
python manage.py createsuperuser
```

### Загрузите статику:

```bash
python manage.py collectstatic --no-input
```

### Заполните базу тестовыми данными:

```bash
python manage.py loaddata initial_data.json
```

- Запустите сервер 
```bash
python manage.py runserver
```

## Полный запуск проекта

- Создайте файл .env в папке проекта:

```.env
SECRET_KEY="..."                      # ваш ключ (get_random_secret_key())
DB_ENGINE=django.db.backends.postgres # указываем postgres
DB_NAME=postgres                      # имя базы данных
POSTGRES_USER=postgres                # логин для подключения к базе
POSTGRES_PASSWORD=password            # пароль для подключения к БД
DB_HOST=db                            # название контейнера
DB_PORT=5432                          # порт для подключения к БД
DEBUG=True                            
```

- Выполните команду сборки контейнеров

```bash
docker compose up -d --build
```
В результате выполнения данной команды должно быть собрано четыре контейнера.

- Для просмотра всех контейнеров используйте команду

```bash
docker container ls -a
```
Получаем список контейнеров

- Выполните миграции:

```bash
docker compose exec backend python manage.py migrate
```

- Создайте суперпользователя:

```bash
docker compose exec backend python manage.py createsureruser
```

- Заполните базу тестовыми данными:

```bash
docker compose exec backend python manage.py loaddata initial_data.json
```

- Загрузите статику

```bash
docker compose exec backend python manage.py collectstatic --no-input
```

### Основные адреса:
127.0.0.1 - Главная 
127.0.0.1/admin - Панель администратора 
127.0.0.1/api/docs/ - Документация к API 

### Автор проекта
Дементьев Андрей
