### 🐞 Bug Report 
### ID - API_001
## 🚀 Summary  
Некорректное отображение названия объявления при получении данных по его ID.

---

## 📌 Steps to Reproduce  
1. Отправить `POST /api/1/item` с тестовым запросом:  

```json
{
    "sellerID": 92229394,
    "name": "Google Pixel 7 Pro",
    "price": 3200,
    "statistics": {
        "contacts": 30,
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

## ❌ Actual Result  
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

