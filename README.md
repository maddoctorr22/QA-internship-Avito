# READ ME

## 🚀 Описание
Этот проект содержит автоматизированные тесты для API микросервиса, отвечающего за управление объявлениями.

### 🔹 Основные функции API:
- Создание объявления (`POST /api/1/item`)
- Получение объявления по идентификатору (`GET /api/1/item/{id}`)
- Получение всех объявлений продавца (`GET /api/1/{sellerId}/item`)
- Получение статистики по объявлению (`GET /api/1/statistic/{id}`)

## 🔧 Установка и запуск тестов
### 1️⃣ Установка зависимостей
```bash
pip3 install pytest
```

### 2️⃣ Запуск тестов
```bash
pytest test_api.py
```

## 📝 Инструкция по тестированию
1. Установите зависимости (`pip3 install pytest`).
2. Запустите тесты с помощью команды `pytest test_api.py`.
3. Проверьте отчёт в консоли.
4. В случае ошибок проверьте лог в `pytest` и зафиксируйте баги в `BUGS.md`.
5. При необходимости обновите тест-кейсы в `TESTCASES.md`.


## 📌 Тестирование
- Тесты написаны с использованием **pytest** и **requests**.
- Проверяются как **позитивные**, так и **негативные** сценарии.
- Используются **фикстуры** для подготовки данных.

## ⚠ Найденные баги
Если в ходе тестирования обнаружены ошибки, они документируются в файле `BUGS.md`.

## 📩 Контакты
Если у вас есть вопросы или предложения, свяжитесь со мной по почте **vitman.vladislav98@gmail.com**.

## PS... ##
К сожалению, не мог уделять заданию достаточно времени по семейным обстоятельствам, чтобы полностью его доделать и довести до ума, и не доделал задание с автоматизацией но надеюсь, вы оцените :)


