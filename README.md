exersice_1 - Функция выводит n первых элементов последовательности 122333444455555… (число повторяется столько раз, чему
оно равно).

exersice_2 - Food Store API. Проект магазина продуктов.

# Food Store API

Это документация API проекта Foo Store. Она предоставляет эндпоинты для управления категориями, продуктами, корзиной и
аутентификацией.

## Стек технологий

API Foo Store разработан с использованием следующих технологий:

- Python
- Django
- Django REST Framework
- PostgreSQL (в качестве базы данных)
- Swagger UI (для документации API)
- ReDoc (для документации API)
-

## Установка

1. Клонируйте репозиторий:

git clone <repository_url>

2. Перейдите в директорию проекта:

cd exersice_2

3. Создайте и активируйте виртуальное окружение (опционально, но рекомендуется):

python -m venv myenv
source myenv/bin/activate

4. Установите зависимости:

pip install -r requirements.txt

5. Настройте базу данных:

Для работы с проектом необходимо наличие и запуск PostgreSQL. Создайте базу данных и добавьте имя базы данных, имя
пользователя и пароль в файл .env (создайте новый файл с этим именем в корневой папке проекта на основе файла
.env_sample).

6. Примените миграции базы данных:

python manage.py migrate

7. Запустите разработческий сервер:

python manage.py runserver

API будет доступно по адресу http://localhost:8000/.

## Эндпоинты API

### Категории

- **GET /api/categories/**

  Получить список всех категорий.

- **POST /api/category/create/**

  Создать новую категорию. Требуется аутентификация.

- **PUT /api/category/edit/{id}/**

  Обновить существующую категорию с указанным id. Требуется аутентификация.

- **DELETE /api/category/delete/{pk}/**

  Удалить категорию с указанным pk. Требуется аутентификация.

### Продукты

- **GET /api/products/**

  Получить список всех продуктов.

- **GET /api/products/{slug}/**

  Получить информацию о конкретном продукте по его слагу.

- **POST /api/products/create/**

  Создать новый продукт. Требуется аутентификация.

- **PUT /api/products/{slug}/update/**

  Обновить существующий продукт с указанным слагом. Требуется аутентификация.

- **DELETE /api/products/{slug}/delete/**

  Удалить продукт с указанным слагом. Требуется аутентификация.

### Корзина

- **GET /api/cart/**

  Получить список товаров в корзине для аутентифицированного пользователя.

- **POST /api/cart/add/**

  Добавить продукт в корзину. Требуется аутентификация.

- **PUT /api/cart/update/{pk}/**

  Обновить количество товара в корзине с указанным pk. Требуется аутентификация.

- **DELETE /api/cart/remove/{pk}/**

  Удалить товар из корзины с указанным pk. Требуется аутентификация.

- **GET /api/cart/summary/**

  Получить сводку корзины, включающую общее количество товаров и общую стоимость. Требуется аутентификация.

### Аутентификация

- **POST /api/token/**

  Получить access token и refresh token, предоставив правильные учетные данные.

- **POST /api/token/refresh/**

  Обновить access token, предоставив действующий refresh token.

### Swagger и ReDoc

- **GET /api/swagger/**

  Документация Swagger UI для API.

- **GET /api/redoc/**

  Документация ReDoc для API.

## Примеры

Вот некоторые примеры использования эндпоинтов API с помощью cURL:

- **GET /api/categories/**

curl -X GET http://localhost:8000/api/categories/

- **POST /api/category/create/**

curl -X POST http://localhost:8000/api/category/create/ -H "Content-Type: application/json" -d '{"name": "Новая
категория"}' -H "Authorization: Bearer <access_token>"

- **PUT /api/category/edit/{id}/**

curl -X PUT http://localhost:8000/api/category/edit/1/ -H "Content-Type: application/json" -d '{"name": "Обновленная
категория"}' -H "Authorization: Bearer <access_token>"

- **DELETE /api/category/delete/{pk}/**

curl -X DELETE http://localhost:8000/api/category/delete/1/ -H "Authorization: Bearer <access_token>"

Обратите внимание, что вам нужно заменить <access_token> на действительный access token, полученный после
аутентификации.