# Лабораторна робота №1
## Аналіз якості програмного продукту. Виявлення та документування аномалій

**Виконав:** Владислав Фесенко
**Група:** 6.1213-2пы
**Дата виконання:** 16.10.2026

## Тестовий об'єкт
SauceDemo - https://www.saucedemo.com/

## Тестове середовище
- Операційна система: Windows 10
- Браузер: Microsoft Edge
- URL: https://www.saucedemo.com/
- Дата тестування: 16.10.2026

## Базовий сценарій
За допомогою standard_user / secret_sauce перевірено:
Login -> Products -> Add to cart -> Cart -> Checkout -> First Name, Last Name, Zip -> Continue -> Finish.
Результат: Thank you for your order! - сценарій успішний.

## Виявлені аномалії

| № | Користувач              | Короткий опис                                          | Severity | Priority | Issue    |
| 1 | performance_glitch_user | Затримка відкриття Products після логіну               | Medium   | Medium   | Issue #1 |
| 2 | problem_user            | Однакове зображення для всіх товарів                   | High     | High     | Issue #2 |
| 3 | problem_user            | Не працює сортування за ціною                          | Medium   | Medium   | Issue #3 |
| 4 | problem_user            | Помилка в полі Last Name, неможливо оформити замовлення| High     | High     | Issue #4 |

## Висновок
В ході роботи визначено еталонну поведінку на standard_user та problem_user виявлено 4 аномалії при порівнянні з іншими користувачами. Аномалії задокументовано за правилом Що? Де? Коли?
