# 03 - PWM Breathing LED

**Дата:** 05.05.2026  
**Рівень:** Beginner / Intermediate  
**Мета:** Навчитися керувати яскравістю LED за допомогою PWM через прямий доступ до регістра CCR.

### Фото збірки
<img width="4032" height="3024" alt="IMG_8946" src="https://github.com/user-attachments/assets/e626ec8d-fa85-430b-a12d-8e979d2aa920" />
<img width="4032" height="3024" alt="IMG_8947" src="https://github.com/user-attachments/assets/335b052f-3310-4105-8046-a6467b0bf311" />

### Посилання на відео роботи
https://streamable.com/61ugmr

### Схема підключення

- **PWM вихід**: **PA6** (TIM3_CH1)
- Зовнішній LED:
  - Довга ніжка (Анод) → резистор 220-330 Ом → **PA6**
  - Коротка ніжка (Катод) → **GND**

### Основний код (`main.c`)

```c
/* USER CODE BEGIN PV */
uint16_t brightness = 0;
int8_t direction = 1;
/* USER CODE END PV */

/* USER CODE BEGIN 2 */
HAL_TIM_PWM_Start(&htim3, TIM_CHANNEL_1);
/* USER CODE END 2 */

while (1)
{
    brightness += direction * 2;

    if (brightness >= 68)
        direction = -1;
    if (brightness <= 3)
        direction = 1;

    TIM3->CCR1 = brightness;        // Прямий доступ до регістра CCR1

    HAL_Delay(20);
}
