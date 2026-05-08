# 04 - UART Debug System (printf через UART)

**Мета:** Налаштувати UART для зручного debug-виведення (аналог printf) на комп'ютер.

### Фото підключення
<img width="4032" height="3024" alt="IMG_8953" src="https://github.com/user-attachments/assets/a1b53a5a-ef17-4222-a07d-ea7aeb19fbeb" />
<img width="1698" height="1054" alt="Знімок екрана 2026-05-08 о 18 46 31" src="https://github.com/user-attachments/assets/15c9e1a9-002a-4bc7-80bc-eb4ef6139fe4" />


### Схема підключення

- **PA9** (TX) → RX на USB-to-UART адаптері
- **PA10** (RX) → TX на USB-to-UART адаптері
- **GND** → GND

**Baud Rate:** 115200

### Основний код

```c
char msg[80];

while (1)
{
    sprintf(msg, "Tick = %lu ms | Hello from STM32 Blue Pill!\r\n", HAL_GetTick());
    HAL_UART_Transmit(&huart1, (uint8_t*)msg, strlen(msg), HAL_MAX_DELAY);

    HAL_Delay(1000);
}
