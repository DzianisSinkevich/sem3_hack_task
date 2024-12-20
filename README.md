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

Датасет: https://github.com/yandex/geo-reviews-dataset-2023, содержит поля:
- *address*: адрес организации.
- *name_ru*: название организации.
- *rubrics*: список рубрик, к которым относится организация.
- *rating*: оценка пользователя (от 0 до 5).
- *text*: текст отзыва.

## Технологии
- [Python](https://www.python.org/)
- [transformers](https://github.com/huggingface/transformers)
- [Google Colab](https://colab.research.google.com/)

## Использование
1. */notebooks/3sem_hackaton_prepare.ipynb*: блокнот с подготовкой данных
2. */notebooks/3sem_hackaton_model_fit.ipynb*: блокнот с обучением модели
3. */notebooks/3sem_hackaton_model_use.ipynb*: блокнот с проверкой работы модели
*возможен произвольный ввод данных(рубрика, рейтинг, ключевые слова), на основе которых модель сгенерирует отзыв.

## Команда проекта
- [Виталий К] — Developer
- [Денис С] — Developer, Орг. вопросы, оформление
- [Юлия Б]— Developer
- [Алёна А] — Исследования, тестирование

## Этапы работы:
- 1 Подготовка
  - 1.1. Подготовка окружения. Импорт библиотек и проч.
  - 1.2. Загрузка данных. Проверка данных, оценка для дальнейшей очистки данных.
  - 1.3. Очистка и подготовка данных
  - 1.4. Выделение ключевых слов
- 2 Обучение модели
  - 2.1. Подготовка окружения. Импорт библиотек и проч
  - 2.2. Загрузка данных
  - 2.3. Обучение модели
- 3 Оценка качества модели
  - 3.1. Анализ перспективы улучшения качества модели

## 1. Подготовка
### 1.1. Импорт библиотек
Для выполнения анализа и обработки данных использованы следующие библиотеки:
- *pandas* - для работы с данными.
- *sklearn* - для кластеризации и анализа TF-IDF.
- *pathlib* - для работы с путями в файлам в Google Drive.

### 1.2. Загрузка и первичная обработка данных
- Датасет был загружен в формате .parquet.
- Вычислена базовая статистика:
  - Количество уникальных организаций, адресов и рубрик.

### 1.3. Очистка и подготовка данных
- Проведена очистка данных:
  - Удалены строки с пропущенными значениями.
  - Удалены дубликаты текстов отзывов.

### 1.4. Выделение ключевых слов
- С помощью TF-IDF анализа были выделены ключевые слова для каждой рубрики.
- Датасет был дополнен новым признаком kw_by_rub — ключевые слова, соответствующие рубрикам организации.

## 2. Обучение модели
Во второй части проекта реализовали дообученнае нейронной сети на основе модели **GPT-2 sberbank-ai/rugpt3small_based_on_gpt2**, которая способна генерировать текстовые отзывы о различных местах.
Для обучения использовались данные, подготовленные нашей командой на первых этапах нашего проекта, включающие очищенные тексты отзывов, категории мест, средние рейтинги и ключевые слова.

### 2.1. Подготовка окружения. Импорт библиотек и проч
Для выполнения задачи использовались следующие библиотеки:
- *datasets* - для работы с форматом данных совместимом с библиотекой transformers.
- *transformers* - для работы с моделью, токенизатором.

### 2.2. Загрузка данных
Данные подготовленные в первом этапе нашего проекта и сохранены в *df_prepare.csv*.
Была осуществлена проверка и удаление строк с пустыми значениями.

### 2.3. Обучение модели
Для дообучения использовалась предобученная модель **sberbank-ai/rugpt3small_based_on_gpt2**. **Дообучение проводилось на мощностях Google Colab Pro с использованием GPU Nvidia A100 и расширенной ОЗУ.**
Обучение модели проводилось с использованием класса Trainer из библиотеки transformers.

## 3. Оценка качества модели
Модель генерирует отзывы, однако качество не высокое. Напрмиер не всегда содержание отзыва соответствует требуемому рейтингу.

### 3.1. Анализ перспективы улучшения качества модели
Для улучшения качества модели могут помочь шаги:
1. Очистить входные данные от эмодзи и других знаков\конструкций.
2. Провести удаление стоп-слов, стемминг и лемматизацию.
3. Провести эксперименты с разными архитектурами и гиперпараметрами модели.

## Заключение
Создана модель, которую можно доработать для генерации отзывов для различных общественных мест, на основании заданных параметров.
