# 02 - Button + LED + Debouncing

**Дата:** 05.05.2026  
**Рівень:** Beginner  
**Мета:** Навчитися працювати з GPIO Input, Pull-up резистором та debounce кнопки.

### Фото збірки
<img width="4032" height="3024" alt="IMG_8926" src="https://github.com/user-attachments/assets/2d28f178-b648-4ed8-8e98-34ea3d754cf5" />
<img width="4032" height="3024" alt="IMG_8925" src="https://github.com/user-attachments/assets/e8a7a6cf-d53d-4d3c-888f-defa32780851" />


### Схема підключення

- **Кнопка**: Один контакт → **PA1**, другий контакт → **GND**
- **LED**: Вбудований на **PC13**

**Важливо:** Використовується внутрішній Pull-up резистор.

### Основний код (`main.c`)

```c
while (1)
{
    if (HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_1) == GPIO_PIN_RESET)  // кнопка натиснута
    {
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_13, GPIO_PIN_SET);    // LED вимкнено (інвертований)
    }
    else
    {
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_13, GPIO_PIN_RESET);  // LED увімкнено
    }

    HAL_Delay(10);  // невелика затримка
}
