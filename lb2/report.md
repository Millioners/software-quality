# Лабораторна робота №2. Проєктування тестів

**Тема:** Проєктування тестів. Checklist, Test Cases та Decision Table
**Сайт для тестування:** https://www.saucedemo.com/

## Test Conditions

- TCND-01 - успішна авторизація валідного користувача;
- TCND-02 - авторизація з неправильним Username;
- TCND-03 - авторизація з неправильним Password;
- TCND-04 - авторизація з порожнім Username;
- TCND-05 - авторизація з порожнім Password;
- TCND-06 - авторизація заблокованого користувача.

## Checklist

- [] Успішна авторизація з валідними даними.
- [] Відмова в авторизації з неправильним Username.
- [] Відмова в авторизації з неправильним Passwoed.
- [] Перевірка порожнього Username.
- [] Перевірка порожнього Password.
- [] Відмова в авторизації заблокованого користувача.

## TC-LOGIN-01 - Успішна авторизація standard_user

**Type:** Positive

**Preconditions:**
- Відкрита сторінка Login;
- користувач не авторизаваний.

**Test Data:**
- Username: standard_user
- Password: secret_sauce

**Steps:**
1. У поле Username ввести standard_user.
2. У поле Password ввести secret_sauce.
3. Натиснути кнопку Login.

**Expected Result:**

Після введеня standard_user і правильного пароля та натискання Login користувач успішно авторизується.

## TC-LOGIN-02 - Авторизація з неправильним Password standard_user

**Type:** Negative

**Preconditions:**
- Відкрита сторінка Login;
- користувач не авторизаваний.

**Test Data:**
- Username: standard_user
- Password: wrong_password 

**Steps:**
1. У поле Username ввести standard_user.
2. У поле Password ввести wrong_password.
3. Натиснути кнопку Login.

**Expected Result:**

Після введення standard_user і неправильного пароля та натискання кнопки Login користувач залишається на сторінці Login зі сповіщенням: «Epic sadface: Username and password do not match any user in this service».

## TC-LOGIN-03 - Авторизація заблокованого користувача locked_out_user

**Type:** Negative

**Preconditions:**
- Відкрита сторінка Login;
- користувач не авторизаваний.

**Test Data:**
- Username: locked_out_user
- Password: secret_sauce 

**Steps:**
1. У поле Username ввести locked_out_user.
2. У поле Password ввести secret_sauce.
3. Натиснути кнопку Login.

**Expected Result:**

Після введення locked_out_user і пароля та натискання кнопки Login користувач залишається на сторінці Login зі сповіщенням: «Epic sadface: Sorry, this user has been locked out.».

## Decision Table

Умови:
- C1: Username входить до списку допустимих?
- C2: Password правильний (secret_sauce)?
- C3: Користувач заблокований?

Дії:
- A1: Перейти до Products
- A2: Показати повідомлення про блокування
- A3: Показати повідомлення про неправильні credentials

|  | R1 | R2 | R3 | R4 | R5 |
| :--- | :---: | :---: | :---: | :---: | :---: |
| C1: Username valid? | T | T | F | T | F |
| C2: Password correct? | T | T | T | F | F |
| C3: User locked? | F | T | - | - | - |
| A1: Products | X |  |  |  |  |
| A2: Locked message |  | X |  |  |  |
| A3: Invalid credentials |  |  | X | X | X |

**Test Cases**

TC-LOGIN-01 (standard_user / secret_sauce) -> це R1
TC-LOGIN-02 (standard_user / wrong_password) -> це R4
TC-LOGIN-03 (locked_out_user / secret_sauce) -> це R2

## 6. Результати виконання
| Test Case ID | Type | Result |
| :--- | :--- | :--- |
| TC-LOGIN-01 | Positive | Pass |
| TC-LOGIN-02 | Negative | Pass |
| TC-LOGIN-03 | Negative | Pass |

## 7. Висновок
В ході роботи було пройдено повний цикл Test Design: від Test Basis до Execution. Визначено 6 Test Conditions, сформовано checklist для швидкої перевірки, створено 3 детальних Test Cases. Decision Table дозволила систематизувати комбінації Username/Password/Blocked та виявити 2 непокриті правила (R3, R5). Всі 3 виконані тести в SauceDemo завершилися з результатом Pass, що підтверджує відповідність реалізації вимогам TB-01 - TB-06.
