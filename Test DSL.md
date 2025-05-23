# Test DSL — Документация

**Test DSL** — это слой в архитектуре Unified App DSL, предназначенный для декларативного описания тестов, включая юнит-тесты, интеграционные тесты, end-to-end сценарии и тесты пользовательского интерфейса. Этот слой делает возможным генерацию кода тестов в соответствии с выбранной технологией.

---

## Цели Test DSL

* Унифицированное описание поведения для верификации
* Поддержка различных уровней тестирования
* Интеграция с Behavior DSL, UI DSL, Interaction DSL
* Генерация кода тестов для Jest, Vitest, Cypress, Flutter test и др.

---

## Основные конструкции DSL

### Юнит-тест

```dsl
tест ПроверкаДобавленияЧисел {
  тип: юнит
  цель: "Сложение двух чисел"
  шаги: [
    вызвать: Сложить(2, 3)
    ожидать: результат == 5
  ]
}
```

### Интеграционный тест

```dsl
tест АвторизацияПользователя {
  тип: интеграция
  цель: "Проверка авторизации через форму"
  шаги: [
    перейти: /вход
    ввести: { поле: email, значение: "user@example.com" }
    ввести: { поле: пароль, значение: "12345678" }
    нажать: Войти
    ожидать: переходНа(/главная)
  ]
}
```

### UI-тест

```dsl
tест ОтображениеОшибкиEmail {
  тип: ui
  цель: "Показ ошибки при некорректном email"
  шаги: [
    перейти: /регистрация
    ввести: { поле: email, значение: "неправильно" }
    потерятьФокус: email
    ожидать: текстНаСтранице("Введите корректный email")
  ]
}
```

---

## Интеграции с другими слоями DSL

| DSL             | Роль                                             |
| --------------- | ------------------------------------------------ |
| Behavior DSL    | Проверка логики и функций                        |
| UI DSL          | Проверка отрисовки компонентов и реакций на ввод |
| Interaction DSL | Проверка событий и сценариев взаимодействия      |
| Validation DSL  | Проверка отображения ошибок валидации            |

---

## Поддержка генерации

Test DSL может быть транспилирован в:

* **Jest / Vitest** (TypeScript)
* **Cypress / Playwright** (E2E)
* **Flutter test** (Dart)
* **JUnit / Espresso** (Android)
* **XCTest** (iOS)

---

## Пример генерации (Jest + Testing Library)

```ts
test("Показ ошибки при некорректном email", () => {
  render(<РегистрацияФорма />)
  userEvent.type(screen.getByLabelText("Email"), "неправильно")
  fireEvent.blur(screen.getByLabelText("Email"))
  expect(screen.getByText("Введите корректный email")).toBeInTheDocument()
})
```

---

## Расширения

* Группировка и сценарии тестов
* Генерация отчётов покрытия
* Запуск в CI/CD
* Интернационализация сообщений об ошибках

