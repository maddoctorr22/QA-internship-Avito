### 🐞 Bug Report 
### ID - API_BUG_001
## Priority
High
## 🚀 Summary  
Некорректное отображение названия объявления при получении данных по его ID.

---

## 📌 Steps to Reproduce  
1. Отправить `POST /api/1/item` с тестовым запросом:  

```json
{
    "sellerID": 228322,
    "name": "Google Pixel 7 Pro",
    "price": 3200,
    "statistics": {
        "contacts": 1000,
        "likes": 322,
        "viewCount": 228
    }
}
```

2. Получить ID созданного объявления из ответа.  
3. Отправить `GET /api/1/item/{id}` с id, полученным в шаге 2.  
4. Проверить поле `name` в ответе.  

---

## ✅ Expected Result  
Поле `name` в ответе `GET /api/1/item/{id}` должно содержать значение, переданное в `POST /api/1/item`.

---

## 🔎  Actual Result  
Поле `name` содержит `"dsds"` вместо `"Google Pixel 7 Pro"`.

```json
{
    "createdAt": "2025-02-15T09:41:18.318640+0300",
    "id": "fec82654-df10-4745-97aa-66fec84462b9",
    "name": "dsds",
    "price": 3200,
    "sellerId": 92229394,
    "statistics": {
        "contacts": 30,
        "likes": 322,
        "viewCount": 228
    }
}

```

---

## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1
---

## 🐞 Bug Report 
## ID - API_BUG_002
## Priority
High
## 🚀 Summary  
**API не проверяет обязательные поля при создании объявления и возвращает `200 OK` вместо `400 Bad Request`, что приводит к созданию некорректных записей в системе.**

---

## 📌 Steps to Reproduce  
1. Отправить `POST /api/1/item` с тестовым запросом:  

```json
{
    "sellerId": 228322,
    "price": 3200,
    "statistics": {
        "contacts": 1000,
        "likes": 322,
        "viewCount": 228
    }
}
```
2. Получить ID созданного объявления из ответа.  
3. Отправить `GET /api/1/item/{id}` с id, полученным в шаге 2.  
4. Проверить поле `name` в ответе.
5. Повторить шаги 1-3, отправляя `POST /api/1/item` без следующих обязательных полей:
   - Убрать `"sellerId"`, отправить запрос.
   - Убрать `"price"`, отправить запрос.
   - Убрать `"statistics"`, отправить запрос.
6. Проверить, что объявления создаются даже без обязательных полей.
   
---

## ✅ Expected Result  
- При отсутствии любого из обязательных полей (`name`, `sellerId`, `price`, `statistics`)
  должен возвращаться код `400 Bad Request`.
- Тело ответа (пример):
  
```json
{
  "status": "400",
  "message": "Field 'name' is required"
}
```

---

## 🔎  Actual Result
- Статус код - `200 OK`
- Тело ответа:
```json
{
    "status": "Сохранили объявление - fd78a915-448d-45cb-b26b-6b00f0a1cdb3"
}
```
## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1
---

## 🐞 Bug Report 
## ID - API_BUG_003
## Priority
High
## 🚀 Summary  
**API принимает метод POST с пустым `Body`, возвращает статус-код `200 OK`**

---

## 📌 Steps to Reproduce  
1. Отправить `POST /api/1/item` с тестовым запросом:  

```json
{}
```
2. Убедиться, что статус-код `200 OK`, получен
---

## ✅ Expected Result  
- Статус-код `400 Bad Request`
- Тело ответа (пример):
  
```json
{
    "result": {
        "message": "",
        "messages": {}
    },
    "status": "не передан объект - объявление"
}
```

## 🔎  Actual Result
- Статус код - `200 OK`
- Тело ответа:
```json
{
    "status": "Сохранили объявление - fd78a915-448d-45cb-b26b-6b00f0a1cdb3"
}
```
## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1
---

## 🐞 Bug Report 
## ID - API_BUG_004
## Priority
Major
## 🚀 Summary  
**API не проверяет значения обязательных полей при создании объявления и возвращает `200 OK` вместо `400 Bad Request`, что приводит к созданию некорректных объявлений в системе.**
---
## 📌 Steps to Reproduce  
1. Отправить `POST /api/1/item` с телом:  
```json
{
    "sellerId": -256,
    "name": "Google Pixel 7 Pro",
    "price": 3200,
    "statistics": {
        "contacts": 1000,
        "likes": 322,
        "viewCount": 228
    }
}
```
2. Получить ID созданного объявления из ответа.  
3. Отправить `GET /api/1/item/{id}` с id, полученным в шаге 2.  
4. Повторить шаги 1-3, отправляя `POST /api/1/item` со следующими данными в полях:
   - `"name": " "`, отправить запрос.
   - `"price": -1`, отправить запрос.
   - `statistics: {}`, отправить запрос.
5. Убедиться, что статус код `200 OK`, получен для всех запросов.
   
---

## ✅ Expected Result  
- Для каждого запроса обязательных полей (`name`, `sellerId`, `price`, `statistics`)
  должен возвращаться код `400 Bad Request`.
- Тело ответа (пример):
  
```json
{
  "status": "400",
  "message": "The 'name' field is invalid"
}
```

---

## 🔎  Actual Result
- Статус код - `200 OK`
- Тело ответа для всех запросов:
```json
{
    "status": "Сохранили объявление - fd78a915-448d-45cb-b26b-6b00f0a1cdb3"
}
```
## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1

## 🐞 Bug Report 
## ID - API_BUG_005

## Priority
High

## 🚀 Summary  

**GET /api/1/item/:id возвращает `createdAt` и `name`, отличающиеся от значений, переданных в POST**

## 📌 Steps to Reproduce
1. Создать объявление через POST /api/1/item с корректными данными.
2. Получить ID из ответа.
3. Запросить объявление GET /api/1/item/{id}.
4. Сравнить name, createdAt с отправленными в POST.
5. Сравнить все поля ответа GET с ожидаемыми значениями из POST:
    createdAt (формат ISO 8601)
    id (совпадает с POST)
    name (совпадает с POST)
    price (совпадает с POST)
    sellerId (совпадает с POST)
    statistics содержит:
    contacts (совпадает с POST)
    likes (совпадает с POST)
    viewCount (совпадает с POST)
---

## ✅ Expected Result  
- Статус-код `200 OK`
```json
 {
    "createdAt": "2025-02-15T17:03:05.777+03:00",
     "id": "89463afe-5bfa-47d1-bc11-f6dd9e2008ce",
     "name": "Google Pixel 7 Pro",
     "price": 3200,
     "sellerId": 228322,
     "statistics": {
         "contacts": 100,
         "likes": 228,
         "viewCount": 322
     }
}
```

## 🔎  Actual Result
- Статус код - `200 OK`
- `name` не совпадает с POST
- `createdAt` должно быть в формате ISO 8601 (YYYY-MM-DDTHH:MM:SS.sssZ)
```json
{
  "createdAt": "2025-02-15 15:48:53.367538 +0300 +0300",  //  Некорректный формат, должно быть ISO 8601
  "id": "b7940f8d-66d4-41d4-a8f7-ea6eb137fed8",
  "name": "dsdsd",  //  Ожидалось "Google Pixel 7 Pro"
  "price": 3200,
  "sellerId": 228322,
  "statistics": {
    "contacts": 100,
    "likes": 228,
    "viewCount": 322
  }
}
```
## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1

- ## 🐞 Bug Report 
## ID - API_BUG_006

## Priority
High
## 🚀 Summary  

**GET /api/1/statistic/{id} возвращает `likes` и `viewCount`, отличающиеся от значений, переданных в POST**

## 📌 Steps to Reproduce
1. Создать объявление через `POST /api/1/item` с корректными данными.
2. Получить ID из ответа.
3. Запросить объявление `GET /api/1/statistic/{id}`.
4. Сравнить все поля ответа GET с ожидаемыми значениями из POST:
    statistics содержит:
    contacts (совпадает с POST)
    likes (совпадает с POST)
    viewCount (совпадает с POST)
---

## ✅ Expected Result  
- Статус-код `200 OK`
```json
 {
     "contacts": 100,
     "likes": 228,
     "viewCount": 322
}
```

## 🔎  Actual Result
- Статус код - `200 OK`
- `likes` не совпадает с POST
- `viewCount` не совпадает с POST
```json
{
    "contacts": 100,
    "likes": 456,
    "viewCount": 778
}
```
## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1

## 🐞 Bug Report 
## ID - API_BUG_007

## Priority
High
## 🚀 Summary  

**GET /api/1/{sellerId}/item возвращает некорректные значения `createdAt`, `id`, `name` в ответе**

## 📌 Steps to Reproduce
1. Создать объявление через POST /api/1/item с корректными данными.
2. Получить sellerId из ответа.
3. Запросить список объявлений продавца GET /api/1/{sellerId}/item.
4. Сравнить все поля ответа GET с ожидаемыми значениями из POST:
    createdAt (формат ISO 8601)
    id (совпадает с POST)
    name (совпадает с POST)
    price (совпадает с POST)
    sellerId (совпадает с POST)
    statistics содержит:
    contacts (совпадает с POST)
    likes (совпадает с POST)
    viewCount (совпадает с POST)
---

## ✅ Expected Result  
- Статус-код `200 OK`
```json
{
    "createdAt": "2025-02-15T17:03:05.777+03:00",
    "id": "89463afe-5bfa-47d1-bc11-f6dd9e2008ce",
    "name": "Google Pixel 7 Pro",
    "price": 3200,
    "sellerId": 228322,
    "statistics": {
        "contacts": 100,
        "likes": 228,
        "viewCount": 322
    }
}
```

## 🔎  Actual Result
- Статус код - `200 OK`
- `createdAt` не совпадает с POST
- `id` не совпадает с POST
- `name` не совпадает с POST
```json
{
    "createdAt": "2025-02-15 11:31:26.222894 +0300 +0300",  //  Некорректный формат, должно быть ISO 8601
    "id": "dsdsd",  //  Ожидалось "89463afe-5bfa-47d1-bc11-f6dd9e2008ce"
    "name": "89463afe-5bfa-47d1-bc11-f6dd9e2008ce",  //  Ожидалось "Google Pixel 7 Pro"
    "price": 3200,
    "sellerId": 228322,
    "statistics": {
        "contacts": 100,
        "likes": 228,
        "viewCount": 322
    }
}
```
## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1

- ## 🐞 Bug Report 
## ID - API_BUG_008

## Priority
High
## 🚀 Summary  

**GET /api/1/{sellerId}/item неверно обрабатывает граничные значения id**

## 📌 Steps to Reproduce
1.Отправить GET-запрос на /api/1/{sellerId}/item с некорректными значениями sellerId:
    `sellerId = 111110 (меньше минимального)`
    `sellerId = 1000000 (больше максимального)`

2.Убедиться, что API возвращает статус-код 400 Bad Request и сообщение об ошибке.
---

## ✅ Expected Result  

- Статус-код `400 Bad Requst`
- Тело ответа содержит сообщение об ошибке:
  
```json
{
    "result": {
        "message": "Передан некорректный идентификатор продавца",
        "messages": {}
    },
    "status": "400"
}
```

## 🔎  Actual Result
- Статус-код: 200 OK
- API не валидирует некорректный sellerId, вместо ошибки возвращает пустой список или некорректные данные.
- Примеры некорректных ответов:
```json
    {
        "createdAt": "2024-09-07 19:47:07.458305 +0300 +0300",
        "id": "Телефон", // ожидалось 9af01064-c385-4ba9-be4f-50d9ba8a21de
        "name": "9af01064-c385-4ba9-be4f-50d9ba8a21de" // ожидалось телефон,
        "price": 700,
        "sellerId": 111110, // айди меньше диапазона
        "statistics": {
            "contacts": 32,
            "likes": 0,
            "viewCount": 14
        }
    }
```
## 🖥 Environment  
- **API Base URL**: https://qa-internship.avito.com  
- **OS**: Windows 10
- **Tool**: Postman 11.32.1
