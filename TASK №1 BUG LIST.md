### **🐞 Баг 1: Ошибка загрузки уведомления (Справа вверху)**

**Приоритет:** `medium`

**Описание:** Возможно, ошибка загрузки контента или проблема на сервере. 

**Шаги для проверки:**
- Открыть DevTools (`F12` → `Console`) и проверить наличие ошибок.
- Перейти во вкладку `Network` и посмотреть неудачные запросы.

---

### **🐞 Баг 2: Визуальный баг — стрелка в фильтрах**

**Приоритет:** `low`

**Описание:** В фильтре "Велосипеды" стрелочка должна быть направлена вниз, так как категория уже выбрана.

---

### **🐞 Баг 3: Ошибка сортировки (Географическое расположение)**

**Приоритет:** `medium`

**Описание:** Переключатель сортировки работает некорректно: сначала идут объявления из Москвы, затем другие регионы, затем снова Москва.
**Ожидаемый результат:** Сортировка должна быть последовательной. Сначала ВСЯ Москва, потом другие

---

### **🐞 Баг 4: Ошибка сортировки (Цена)**

**Приоритет:** `medium`

**Описание:** Элемент сортировки "Дороже/дешевле" работает некорректно.
**Ожидаемый результат:** Товары должны упорядочиваться по цене в выбранном порядке.

---

### **🐞 Баг 5: Ошибка отображения вариантов товаров**

**Приоритет:** `medium`

**Описание:** Выбран ли вариант отображения "с картой" – неясно. Однако товары отображаются "блоками", но при этом средний переключатель ("Блоками") неактивен.
**Ожидаемый результат:** Если отображение товаров идет "Блоками", соответствующий вариант должен быть активен.

---

### **🐞 Баг 6: Некорректное отображение количества страниц**

**Приоритет:** `medium`

**Описание:** Всего найдено **61 товар** (без фильтров). На 1 странице показывается **12 товаров**, но при делении `61/12 = 5.08`, что значит, что должно быть **6 страниц** (5 полных и 1 неполная). 
**Фактический результат:** Отображается 100 страниц. Количество страниц отображается некорректно.

---

### **🐞 Баг 7: Некорректный фильтр "Выбор пола"**

**Приоритет:** `low`

**Описание:** Фильтр "Выбор пола" не имеет смысла для категории "Велосипеды".
**Ожидаемый результат:** Фильтр должен применяться только к соответствующим категориям.

---

### **🐞 Баг 8: Ошибка в названии "Все категории"**

**Приоритет:** `low`

**Описание:** Неверное написание – "Все категори" вместо "Все категории".
**Ожидаемый результат:** Корректное отображение текста "Все категори".

---

### **🐞 Баг 9: Неверное применение фильтров**

**Приоритет:** `medium`

**Описание:** Всего 61 товар, в левом меню фильтров можно показать только 9, хотя там нет никаких примененных фильтров которые
 могут так сильно сократить кол-во товара, кроме диапазона цены в 90.000, но на 1 странице уже как минимум 10 товаров с 
ценой ниже 90.000 

---

### **🐞 Баг 10: Ошибка поиска по бренду**

**Приоритет:** `medium`

**Описание:** Если учитывать что запрос был на велосипеды конкретного бренда их нашло 61, поиск выдал и другие велосипеды, т.е
 поиск работает не верно и неизвесно сколько еще он нашел неверных результатов т.к доступна только 1 страница

**Ожидаемый результат:** В результатах поиска должны быть **только товары указанного бренда**.

---

📩 **Если требуется дополнительная информация, свяжитесь со мной.**
