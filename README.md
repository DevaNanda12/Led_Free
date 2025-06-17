# STM32 Nucleo F446RE LED Blinking with FreeRTOS

This project demonstrates how to blink an onboard LED (connected to pin **PA5**) on the STM32 Nucleo F446RE board using **FreeRTOS**. It creates two concurrent tasks, each toggling the LED at different intervals, showcasing basic RTOS multitasking.

---

## Description

The main program initializes the MCU, sets up system clocks, configures GPIO for the LED pin, and then starts the FreeRTOS scheduler. Two separate tasks are created:

- **defaultTask**: Toggles the LED every 200 milliseconds.
- **LedTask**: Toggles the LED every 1000 milliseconds (1 second).

The tasks run concurrently, causing the LED to toggle at combined intervals as controlled by the RTOS scheduler.

### Key Points of the Code

- **HAL Initialization**: Initializes the hardware abstraction layer and system clocks (using internal HSI oscillator).
- **GPIO Setup**: Configures pin PA5 as push-pull output, initially set LOW.
- **FreeRTOS Setup**:  
  - Two threads/tasks (`defaultTask` and `LedTask`) are created with normal priority and stack size 128 bytes.  
  - The scheduler (`osKernelStart()`) takes control to manage multitasking.
- **Task Functions**:  
  - `StartDefaultTask`: toggles the LED every 200 ms using `HAL_GPIO_TogglePin()` and delays using `osDelay(200)`.  
  - `StartLedTask`: toggles the LED every 1000 ms with a similar approach.
- **Error Handling**: Infinite loop in case of errors.
- **Assertion**: Provides debugging support if full assert is enabled.

---

## Hardware Used

- STM32 Nucleo F446RE development board
- Onboard LED connected to GPIO pin PA5

---

## Software & Tools

- STM32CubeIDE
- STM32Cube HAL library
- FreeRTOS (CMSIS-OS wrapper)

---

## How to Use

1. Clone or download the project.
2. Open the project in STM32CubeIDE.
3. Build and flash the firmware to the STM32 Nucleo F446RE board.
4. Observe the onboard LED blinking with toggling intervals controlled by two RTOS tasks.

---

## Summary

This example is a simple demonstration of using FreeRTOS on STM32 MCUs to run multiple tasks simultaneously, managing LED toggling at different speeds. It’s a foundation to build more complex RTOS-based embedded applications.

---
## Author

- Deva Nanda S
