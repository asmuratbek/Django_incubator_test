# Django_incubator_test

## Тестовое задание

Реализовать модуль каталога.
"Каталог" состоит из "товаров" и "корзины". У "товара" есть:

* Название
* Описание
* Базовая цена
* Порядок сортировки

У каждого "товара" есть:

* "изображения":
  * Файл
  * Подпись
  * Порядок сортировки

* "параметры":
  * Название
  * Значение
  * Цена
  * Порядок сортировки

* "корзина*:
  * фото товара
  * название
  * количество
  * цена
  * итоговая цена(должна формироваться с количества и цены)
  * в корзину можно добавлять разные товары
  

Должна быть возможность редактирования каталога через [Django Admin](https://docs.djangoproject.com/en/3.2/ref/contrib/admin/)

Вывод каталога должен быть в [REST](https://www.django-rest-framework.org/):

* список товаров
* детальная информация по товару

## Системные требования к реализации

* Python 3.8 и выше
* Django 3.2
* Можно использовать любые доступные публично сторонние модули
* PostgreSQL 13 и выше
* Вместе с реализацией должны быть придоставлены [фикстуры с тестовыми данными](https://docs.djangoproject.com/en/3.2/howto/initial-data/) в модуле "каталог"
* Redis 5 и выше

## Запуск проекта

Для запуска проекта необходимо создать файл `settings/local.py` с, примерно, таким содержимым:

```python
# ****************************************************************
# DJANGO

# DATABASES
from .core import DATABASES  # noqa
DATABASES['default']['PASSWORD'] = 'ПАРОЛЬ-К-БАЗЕ-ДАННЫХ'

# DEBUG
# https://docs.djangoproject.com/en/3.2/ref/settings/#debug
from .core import TEMPLATES  # noqa
DEBUG = True
INTERNAL_IPS = ('127.0.0.1', 'localhost')
TEMPLATES[0]['OPTIONS'].update({'debug': DEBUG})
ALLOWED_HOSTS = ['*']

# EMAIL
EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'

# ****************************************************************
# THIRD-PARTY

```

В нём нужно добавить / поправить конфигурацию под своё окружение.

## Проверка тестового задания

* **Выполненное задание будет проверяться на Linux**
* Все сторонние модули должны быть прописаны в файле `requirements.txt`

## Бонусный уровень

Плюсом будет выполнение дополнительных требований:

* список товаров будет фильтроваться по параметрам: по названию и по значению
* отдельно будет отдаваться список параметров для фильтрации:
    - только те параметры, которые есть хотя бы у одного товара
    - у каждого параметра будет список его уникальных значений
    - каждый параметр будет знать, у скольких товаров он есть (просто, поле с числом)
* у каждого товара есть вложенные старницы с параметрами и изображениями
