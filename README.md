Анализ эффективности государственной поддержки российского кинопроизводства и зрительского спроса

## 🎯 Цель проекта

Исследование рынка российского кинопроката для Министерства культуры РФ с акцентом на эффективность государственной поддержки. Проект отвечает на вопросы:
- Какова динамика производства фильмов с господдержкой?
- Какие жанры и студии получают наибольшее финансирование?
- Коррелирует ли размер поддержки с кассовыми сборами?
- Как зрители оценивают субсидируемые фильмы?

## 💡 Использованные технологии

- Python 3.x
- pandas
- matplotlib (для визуализаций)
- Jupyter Notebook

## 🧪 Как запустить проект

```bash
git clone https://github.com/kagor4/Russian-Film-Industry-Analytics.git
cd Russian-Film-Industry-Analytics
pip install -r requirements.txt
```

Затем откройте и запустите файл `Russian_Film_Industry_Analytics.py` или ноутбук `Russian_Film_Industry_Analytics.ipynb` в Jupyter. Убедитесь, что датасеты `mkrf_movies.csv` и `mkrf_shows.csv` доступны в папке `/datasets/`.

## 📊 Описание данных

Данные взяты из портала открытых данных Минкультуры и КиноПоиска:
- **mkrf_movies** (реестр прокатных удостоверений):
  - `title`, `puNumber` — название и номер прокатного удостоверения
  - `show_start_date` — дата премьеры
  - `type`, `film_studio`, `production_country` — тип фильма, студия, страна
  - `refundable_support`, `nonrefundable_support` — объём господдержки
  - `ratings`, `genres` — рейтинг и жанры (КиноПоиск)
- **mkrf_shows** (кассовые сборы):
  - `puNumber`, `box_office` — номер удостоверения и сборы

**Предобработка**:
- Объединение таблиц по `puNumber` с сохранением всех записей из `mkrf_movies`.
- Изменение типов: `show_start_date` → `datetime`, `ratings` → `float` (с обработкой процентов), `puNumber` → `numeric`.
- Пропуски: удалены в `puNumber`, `film_studio`, `production_country`, `director` (мало); заполнены нулями в `refundable_support`, `nonrefundable_support`; оставлены в `budget`, `financing_source`, `genres`, `box_office` (большой объём).
- Дубликаты: удалены 2 дубликата по `puNumber`.
- Категориальные данные: устранены пробелы в `type`, унифицированы разделители в `production_country`.
- Добавлены столбцы: `show_start_year`, `main_director`, `primary_genre`, `proportion_of_government_support`.

## 🔍 Краткие результаты

- **Динамика проката**:
  - Доля фильмов с данными о сборах: 42% за весь период.
  - До 2014 года доля низкая, с 2015 года резко растёт (возможно, из-за нового закона о контроле киноиндустрии).
  - Минимальные сборы: 2010 год; максимальные: 2018 год.
  - Самый успешный год по средним и медианным сборам: 2017.
- **Возрастные ограничения (2015–2019)**:
  - Фильмы «16+» лидируют по сборам (2016–2018).
  - В 2015 году лидировали «12+», в 2019 году лидерство нестабильно (возможно, из-за неполной передачи данных).
- **Государственная поддержка**:
  - Средняя поддержка: возвратная ~10.3 млн руб., невозвратная ~17.3 млн руб.
  - Более половины фильмов имеют бюджет ниже среднего, но рейтинг выше среднего (5.74, медиана 5.85).
  - Лучшая окупаемость у фильмов с рейтингом ~7.00.
- **Выводы**:
  - Господдержка не всегда коррелирует с высокими сборами.
  - Фильмы «16+» наиболее прибыльны, но требуют таргетинга.
  - Рекомендации: перераспределить финансирование, поддерживая студии и режиссёров с высоким рейтингом/окупаемостью.

## 📁 Структура проекта

```
📦 Russian-Film-Industry-Analytics/
├── Russian_Film_Industry_Analytics.py  # анализ и предобработка
├── Russian_Film_Industry_Analytics.ipynb  # Jupyter Notebook
├── requirements.txt               # зависимости
└── README.md                      # описание проекта
```

## ✅ TODO

- Построить ML-модель для предсказания рейтинга фильма
- Провести кластеризацию фильмов по эффективности вложений
- Добавить визуализации по жанрам и студиям
- Разработать Streamlit-приложение для интерактивного анализа

## © Автор

Автор: [kagor4](https://github.com/kagor4)
```
