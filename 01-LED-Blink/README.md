# 01 - LED Blink (Hello World + Clock Configuration)

**Дата:** 05.05.2026  
**Рівень:** Beginner  
**Мета:** Перший проект на STM32 Blue Pill — запустити вбудований LED і правильно налаштувати системний clock.

### Фото збірки
<img width="4032" height="3024" alt="IMG_8922" src="https://github.com/user-attachments/assets/5a95c77a-6309-45df-89c8-b8c6dc866bc6" />


### Що було зроблено:
- Налаштовано зовнішній/внутрішній осцилятор (HSE + PLL)
- Піднято системну частоту до **32 MHz**
- Налаштовано GPIO PC13 як Output
- Реалізовано простий Blink за допомогою `HAL_GPIO_TogglePin()` та `HAL_Delay()`

### Основний код (`main.c`)

```c
while (1)
{
    HAL_GPIO_TogglePin(GPIOC, GPIO_PIN_13);  // Вбудований LED на Blue Pill
    HAL_Delay(500);                          // 500 мс затримка
}
