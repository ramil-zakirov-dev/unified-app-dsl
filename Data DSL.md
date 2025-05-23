# Data DSL — Документация

**Data DSL** — это слой в Unified App DSL, отвечающий за декларативное описание данных, структур, связей и ограничений.

---

## Цели Data DSL

* Централизованное описание доменной модели
* Генерация кода (базы данных, API, GraphQL, Prisma, ORM)
* Связь с валидацией, UI и тестами

---

## Базовые конструкции

### Сущности

```dsl
сущность Пользователь {
  идентификатор: uuid
  имя: строка
  электронная_почта: email
  роль: перечисление(Клиент, Ресторан, Курьер, Админ)
  создан: datetime
}

сущность Блюдо {
  идентификатор: uuid
  название: строка
  описание: текст
  цена: число
  ресторан: связь к Пользователь
  изображение: строка
}

сущность Заказ {
  идентификатор: uuid
  клиент: связь к Пользователь
  блюда: список связи к Блюдо
  адрес: строка
  статус: перечисление(Создан, Подтвержден, В пути, Доставлен, Отменен)
  сумма: число
  создан: datetime
  курьер: связь к Пользователь
}

сущность Корзина {
  идентификатор: uuid
  клиент: связь к Пользователь
  блюда: список связи к Блюдо
  сумма: число
  обновлен: datetime
}
```

### Связи

```dsl
сущность Заявка {
  идентификатор: uuid
  клиент: связь к Пользователь
  описание: текст
  статус: перечисление(Новая, В работе, Завершена)
  создан: datetime
}
```

---

## Поддерживаемые типы

* `строка`, `текст`, `число`, `дата`, `datetime`, `email`, `телефон`
* `перечисление(...)` для перечислений
* `uuid`, `id`, `логический`
* `json`, `массив`, `связь`

---

## Валидация

```dsl
сущность Сообщение {
  текст: текст {
    обязательно
    мин: 1
    макс: 1000
  }
  автор: связь к Пользователь
}
```

---

## Связь с другими DSL

| DSL              | Роль                                     |
| ---------------- | ---------------------------------------- |
| Logic / Behavior | Получает и обновляет данные через методы |
| UI DSL           | Отражение полей в формах, инпутах        |
| Test DSL         | Создание тестов с исходными данными      |
| Validation DSL   | Получает описания правил                 |

---

## Возможные расширения

* Импорт/экспорт схем
* Автогенерация API/CRUD/валидаторов
* Схемы для аналитики и складов

---
