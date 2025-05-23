# Unified App DSL

**Unified App DSL** — это человекоориентированный язык для декларативного описания приложений. Его цель — упростить проектирование, разработку и сопровождение современных цифровых продуктов за счёт многоуровневой архитектуры, где каждый слой отвечает за определённый аспект приложения. Язык предназначен для специалистов разного профиля: от аналитиков и дизайнеров до разработчиков и тестировщиков.

## Архитектура и слои DSL

Проект разделён на несколько специализированных DSL-слоёв, каждый из которых документирован отдельным файлом:

1. **Natural Language Layer (Zero Syntax)**
   - Описание приложений на естественном языке.
   - Служит отправной точкой для генерации структурированных слоёв DSL.
   - Доступен для нетехнических специалистов.

2. **Product DSL**
   - Декларативное описание структуры продукта: фичи, роли, тарифы, сегменты пользователей, продуктовая логика.
   - Связывает бизнес-цели с функциональными слоями приложения.

3. **UI DSL**
   - Описание пользовательского интерфейса, его компонентов и визуальных элементов.
   - Фокус на компонентной структуре и стилизации.

4. **Layout DSL**
   - Описание структуры, расположения и адаптивности элементов интерфейса.
   - Отделяет визуальное расположение от логики и данных.

5. **Interaction DSL**
   - Описание пользовательских взаимодействий, событий, переходов, анимаций и состояний.
   - Связывает UI и бизнес-логику.

6. **Behavior and Logic DSL**
   - Описание бизнес-правил, условий, реакций на события, методов и потоков логики приложения.
   - Интеграция с Data DSL, UI DSL, Interaction DSL.

7. **Data DSL**
   - Декларативное описание данных, структур, связей и ограничений.
   - Поддержка генерации кода для БД, API, ORM и т.д.

8. **Validation DSL**
   - Описание правил валидации данных и форм.
   - Единый источник правды для проверки данных на клиенте и сервере.

9. **Animation DSL**
   - Описание анимаций и переходов для интерфейса и взаимодействий.
   - Поддержка различных платформ (Web, Flutter и др.).

10. **Integration DSL**
    - Описание и использование внешних сервисов: e-mail, SMS, платежи, push-уведомления и др.
    - Централизованное описание сторонних API.

11. **Metrics DSL**
    - Декларативное описание ключевых метрик продукта, аналитики и A/B тестирования.
    - Связь с Behavior DSL, Product DSL и Test DSL.

12. **Test DSL**
    - Декларативное описание тестов: юнит, интеграционные, e2e, UI-тесты.
    - Генерация кода тестов для различных технологий.

---

## Ключевые особенности

- **Многоуровневая архитектура**: Каждый аспект приложения описывается на своём уровне, что облегчает поддержку и развитие.
- **Интеграция между слоями**: Слои DSL тесно связаны между собой, обеспечивая целостность и переиспользуемость описаний.
- **Человекочитаемость**: Язык ориентирован на простое и понятное описание, снижая барьер между бизнесом и разработкой.
- **Расширяемость**: Возможность добавления новых слоёв и интеграций без нарушения общей структуры.

---

## Пример сценария использования

1. Описание требований к продукту на естественном языке (Natural Language Layer).
2. Генерация Product DSL и других слоёв на основе этого описания.
3. Декларативное описание UI, логики, данных, интеграций и тестов.
4. Автоматическая генерация кода, тестов, конфигов аналитики и документации.

---