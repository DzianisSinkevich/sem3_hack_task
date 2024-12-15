# Хакатон. Учебная задача
## Содержание
- [Описание](#описание)
- [Технологии](#технологии)
- [Использование](#использование)
- [Проблемы и решения](#возможные-проблемы-и-их-решения)
- [Команда проекта](#команда-проекта)

## Описание
Цель проекта: создание нейронной сети, которая способна генерировать текстовые отзывы об общественных местах на основе задаваемых параметрах. Например: категория места, средний рейтинг и ключевые слова. 
Для этого проведен анализ и подготовка данных.

Данные для проекта взяты из открытого датасета отзывов на организации в России, доступного на GitHub. Датасет содержит 500 000 уникальных отзывов, опубликованных на Яндекс Картах с января по июль 2023 года.

Данные: https://github.com/yandex/geo-reviews-dataset-2023

## Технологии
- [Python](https://www.python.org/)

## Использование
Датасет: https://github.com/yandex/geo-reviews-dataset-2023
- Датасет содержит следующие столбцы:
- address: Адрес организации.
- name_ru: Название организации.
- rubrics: Список рубрик, к которым относится организация.
- rating: Оценка пользователя (от 0 до 5).
- text: Текст отзыва.

# Контакты и инструкции, как связаться с командой разработки.


## Команда проекта
- [Виталий К] — Developer
- [Денис С] — Developer, Орг. вопросы, оформление
- [Юлия Б]— Developer
- [Алёна А] — Исследования, тестирование

## Этапы работы:
- 1. Подготовка   
- 1.1. Подготовка окружения. Импорт библиотек и проч.
- 1.2. Загрузка данных. Проверка данных, оценка для дальнейшей очистки данных.
- 1.3. Очистка и подготовка данных
- 1.4. Выделение ключевых слов
- 2. Обучение модели
- 2.1. Подготовка окружения. Импорт библиотек и проч
- 2.2. Загрузка данных
- 2.3. Обучение модели
- 3. Оценка качества модели
