---
layout: default
title: "Your Embedded Project Title Here"
description: "Brief description of your embedded project for SEO and social sharing"
date: YYYY-MM-DD
categories: [embedded, microcontroller, project]
tags: [stm32, arduino, embedded-c, hardware]
author: Hồ Thiện Ái
image: /fundamentals/assets/your-project-main-image.png
featured_image: /fundamentals/assets/your-project-featured.jpg
difficulty: beginner|intermediate|advanced
estimated_time: "2-4 giờ"
components:
  - STM32F103C8T6
  - LED
  - Resistor
  - Breadboard
tools:
  - STM32CubeIDE
  - ST-Link Debugger
  - Multimeter
---

# {{ page.title }}

*Ngày đăng: {{ page.date | date: "%d/%m/%Y" }} • Độ khó: {{ page.difficulty }} • Thời gian: {{ page.estimated_time }}*

## Hình ảnh dự án

![{{ page.title }}]({{ page.image }})
*Hình ảnh tổng quan dự án: {{ page.title }}*

---

## Mục lục

1. [Tổng quan dự án](#tổng-quan-dự-án)
2. [Yêu cầu và chuẩn bị](#yêu-cầu-và-chuẩn-bị)
3. [Thiết kế phần cứng](#thiết-kế-phần-cứng)
4. [Thiết lập môi trường phát triển](#thiết-lập-môi-trường-phát-triển)
5. [Lập trình firmware](#lập-trình-firmware)
6. [Testing và Debug](#testing-và-debug)
7. [Kết quả và demo](#kết-quả-và-demo)
8. [Troubleshooting](#troubleshooting)
9. [Phát triển thêm](#phát-triển-thêm)
10. [Kết luận](#kết-luận)

---

## Tổng quan dự án

### Mô tả dự án

![Sơ đồ khối hệ thống](/fundamentals/assets/system-block-diagram.png)
*Sơ đồ khối tổng quan của hệ thống*

Mô tả ngắn gọn về dự án embedded của bạn và mục tiêu cần đạt được:
- Chức năng chính của dự án
- Các tính năng đặc biệt
- Ứng dụng thực tế

### Mục tiêu học tập

Sau khi hoàn thành dự án này, bạn sẽ:
- ✅ Hiểu được cách cấu hình GPIO
- ✅ Nắm vững việc sử dụng timer/interrupt
- ✅ Biết cách debug embedded system
- ✅ Áp dụng được best practices

### Kiến thức tiên quyết

- Lập trình C cơ bản
- Hiểu biết về vi điều khiển
- Kiến thức điện tử cơ bản
- Familiar với datasheet reading

---

## Yêu cầu và chuẩn bị

### Phần cứng cần thiết

![Linh kiện dự án](/fundamentals/assets/components-layout.jpg)
*Các linh kiện cần thiết cho dự án*

**Vi điều khiển:**
{% for component in page.components %}
- {{ component }}
{% endfor %}

**Linh kiện bổ sung:**
- Breadboard mini
- Jumper wires
- USB cable
- External power supply (nếu cần)

### Phần mềm và công cụ

![Môi trường phát triển](/fundamentals/assets/development-environment.png)
*Screenshot môi trường phát triển*

**IDE và Tools:**
{% for tool in page.tools %}
- {{ tool }}
{% endfor %}

**Libraries cần thiết:**
- HAL Library
- CMSIS
- Custom libraries (nếu có)

### Thiết lập workspace

```bash
# Tạo thư mục dự án
mkdir embedded_project
cd embedded_project

# Clone template hoặc tạo project mới
# Instructions cho việc setup
```

---

## Thiết kế phần cứng

### Sơ đồ mạch điện

![Sơ đồ mạch chi tiết](/fundamentals/assets/detailed-circuit-diagram.png)
*Sơ đồ mạch điện chi tiết với pin mapping*

### Bảng kết nối

| Pin MCU | Tên Pin | Kết nối đến | Mô tả chức năng |
|---------|---------|-------------|-----------------|
| PA5     | GPIO_Output | LED Anode | Điều khiển LED chính |
| PA0     | ADC_IN0 | Potentiometer | Đọc giá trị analog |
| PB6     | I2C1_SCL | I2C Clock | Giao tiếp I2C |
| PB7     | I2C1_SDA | I2C Data | Giao tiếp I2C |
| GND     | Ground | Common GND | Chân âm chung |
| 3V3     | Power | VCC | Nguồn 3.3V |

### PCB Layout (nếu có)

![PCB Layout](/fundamentals/assets/pcb-layout.png)
*Layout PCB cho dự án (nếu thiết kế PCB)*

### Power Analysis

- **Điện áp hoạt động:** 3.3V
- **Dòng tiêu thụ:** ~50mA (max)
- **Power consumption:** ~165mW
- **Battery life:** Ước tính với CR2032

---

## Thiết lập môi trường phát triển

### Cấu hình STM32CubeIDE

![CubeIDE Configuration](/fundamentals/assets/cubeide-config.png)
*Screenshot cấu hình project trong STM32CubeIDE*

#### Bước 1: Tạo project mới

```c
// Project settings
MCU: STM32F103C8T6
Project Type: STM32Cube
Toolchain: STM32CubeIDE
```

#### Bước 2: Cấu hình Clock

![Clock Configuration](/fundamentals/assets/clock-config.png)
*Cấu hình clock tree*

#### Bước 3: Pin Configuration

![Pin Configuration](/fundamentals/assets/pin-config.png)
*Cấu hình chân I/O trong CubeMX*

---

## Lập trình firmware

### Cấu trúc project

```
project/
├── Core/
│   ├── Src/
│   │   ├── main.c
│   │   ├── gpio.c
│   │   └── stm32f1xx_it.c
│   └── Inc/
│       ├── main.h
│       └── gpio.h
├── Drivers/
└── Makefile
```

### Initialization Code

```c
// main.c - System initialization
#include "main.h"
#include "gpio.h"

/* Private variables */
ADC_HandleTypeDef hadc1;
TIM_HandleTypeDef htim2;

int main(void)
{
    /* System initialization */
    HAL_Init();
    SystemClock_Config();
    
    /* Peripheral initialization */
    MX_GPIO_Init();
    MX_ADC1_Init();
    MX_TIM2_Init();
    
    /* Start timer */
    HAL_TIM_Base_Start_IT(&htim2);
    
    /* Main loop */
    while (1)
    {
        main_application();
        HAL_Delay(100);
    }
}
```

### GPIO Configuration

![GPIO Setup](/fundamentals/assets/gpio-setup-code.png)
*Screenshot code cấu hình GPIO*

```c
// gpio.c - GPIO configuration
void MX_GPIO_Init(void)
{
    GPIO_InitTypeDef GPIO_InitStruct = {0};
    
    /* GPIO Ports Clock Enable */
    __HAL_RCC_GPIOA_CLK_ENABLE();
    __HAL_RCC_GPIOB_CLK_ENABLE();
    
    /* Configure GPIO pin Output Level */
    HAL_GPIO_WritePin(LED_GPIO_Port, LED_Pin, GPIO_PIN_RESET);
    
    /* Configure GPIO pin : LED_Pin */
    GPIO_InitStruct.Pin = LED_Pin;
    GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
    GPIO_InitStruct.Pull = GPIO_NOPULL;
    GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
    HAL_GPIO_Init(LED_GPIO_Port, &GPIO_InitStruct);
    
    /* Configure GPIO pin : Button_Pin */
    GPIO_InitStruct.Pin = BUTTON_Pin;
    GPIO_InitStruct.Mode = GPIO_MODE_IT_FALLING;
    GPIO_InitStruct.Pull = GPIO_PULLUP;
    HAL_GPIO_Init(BUTTON_GPIO_Port, &GPIO_InitStruct);
    
    /* EXTI interrupt init */
    HAL_NVIC_SetPriority(EXTI0_IRQn, 0, 0);
    HAL_NVIC_EnableIRQ(EXTI0_IRQn);
}
```

### Main Application Logic

```c
// main.c - Application logic
void main_application(void)
{
    static uint32_t adc_value = 0;
    static uint8_t led_state = 0;
    
    /* Read ADC value */
    HAL_ADC_Start(&hadc1);
    if (HAL_ADC_PollForConversion(&hadc1, 100) == HAL_OK) {
        adc_value = HAL_ADC_GetValue(&hadc1);
    }
    HAL_ADC_Stop(&hadc1);
    
    /* Control LED based on ADC value */
    if (adc_value > 2048) {
        led_state = 1;
    } else {
        led_state = 0;
    }
    
    HAL_GPIO_WritePin(LED_GPIO_Port, LED_Pin, led_state);
    
    /* Debug output */
    printf("ADC Value: %lu, LED: %s\n", 
           adc_value, 
           led_state ? "ON" : "OFF");
}
```

### Interrupt Handlers

```c
// stm32f1xx_it.c - Interrupt handlers
void EXTI0_IRQHandler(void)
{
    HAL_GPIO_EXTI_IRQHandler(BUTTON_Pin);
}

void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
    if (GPIO_Pin == BUTTON_Pin) {
        // Button pressed - toggle mode
        toggle_operation_mode();
    }
}

void TIM2_IRQHandler(void)
{
    HAL_TIM_IRQHandler(&htim2);
}

void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
{
    if (htim->Instance == TIM2) {
        // Timer interrupt - periodic task
        update_system_status();
    }
}
```

---

## Testing và Debug

### Unit Testing

![Debug Session](/fundamentals/assets/debug-session.png)
*Screenshot debug session trong IDE*

#### Bước kiểm tra cơ bản

1. **Hardware Check:**
   ```c
   // Test GPIO toggle
   void test_gpio_toggle(void) {
       for(int i = 0; i < 10; i++) {
           HAL_GPIO_TogglePin(LED_GPIO_Port, LED_Pin);
           HAL_Delay(500);
       }
   }
   ```

2. **ADC Test:**
   ```c
   // Test ADC reading
   void test_adc_reading(void) {
       uint32_t adc_val = read_adc_value();
       printf("ADC Value: %lu (%.2fV)\n", 
              adc_val, 
              (adc_val * 3.3f) / 4095.0f);
   }
   ```

### Integration Testing

![Oscilloscope Measurement](/fundamentals/assets/oscilloscope-measurement.jpg)
*Đo tín hiệu bằng oscilloscope*

#### Test Cases

| Test Case | Input | Expected Output | Result |
|-----------|-------|-----------------|--------|
| TC001 | Button Press | LED Toggle | ✅ Pass |
| TC002 | ADC > 2048 | LED ON | ✅ Pass |
| TC003 | ADC < 2048 | LED OFF | ✅ Pass |
| TC004 | Timer Interrupt | Status Update | ✅ Pass |

### Performance Analysis

```c
// Performance measurement
void measure_execution_time(void) {
    uint32_t start_time = HAL_GetTick();
    
    // Execute function to measure
    main_application();
    
    uint32_t execution_time = HAL_GetTick() - start_time;
    printf("Execution time: %lu ms\n", execution_time);
}
```

---

## Kết quả và demo

### Video Demo

![Demo Setup](/fundamentals/assets/demo-setup.jpg)
*Setup demo dự án*

[🎥 **Video Demo**](https://youtube.com/demo-link)
*Click để xem video demo hoạt động của dự án*

### Screenshots Results

![Result Screenshot 1](/fundamentals/assets/result-1.png)
*Giao diện monitor serial output*

![Result Screenshot 2](/fundamentals/assets/result-2.jpg)
*Hình ảnh dự án hoạt động thực tế*

### Performance Metrics

| Metric | Value | Unit |
|--------|-------|------|
| Response Time | < 10 | ms |
| CPU Usage | ~15 | % |
| Memory Usage | 2.1 | KB |
| Power Consumption | 45 | mA |

---

## Troubleshooting

### Vấn đề thường gặp

![Troubleshooting Guide](/fundamentals/assets/troubleshooting-flowchart.png)
*Flowchart troubleshooting*

| Vấn đề | Nguyên nhân có thể | Giải pháp |
|--------|-------------------|-----------|
| LED không sáng | Kết nối sai, GPIO config | Kiểm tra wiring, review code |
| ADC đọc sai | Reference voltage, calibration | Check VREF, calibrate ADC |
| Code không compile | Missing libraries, syntax | Check includes, fix syntax |
| Debug không connect | ST-Link driver, connection | Update driver, check cable |

### Debug Tips

```c
// Debug macros
#ifdef DEBUG
    #define DBG_PRINT(fmt, ...) printf(fmt, ##__VA_ARGS__)
#else
    #define DBG_PRINT(fmt, ...)
#endif

// Assert macro
#define ASSERT(condition) \
    if(!(condition)) { \
        printf("ASSERT FAILED: %s:%d\n", __FILE__, __LINE__); \
        while(1); \
    }
```

---

## Phát triển thêm

### Tính năng mở rộng

![Feature Roadmap](/fundamentals/assets/feature-roadmap.png)
*Roadmap phát triển các tính năng*

#### Phase 1: Basic Features ✅
- [x] GPIO control
- [x] ADC reading
- [x] Timer interrupt

#### Phase 2: Advanced Features 🚧
- [ ] PWM output control
- [ ] I2C communication
- [ ] UART logging
- [ ] EEPROM data storage

#### Phase 3: IoT Integration 📋
- [ ] WiFi connectivity
- [ ] Cloud data logging
- [ ] Mobile app interface
- [ ] OTA firmware update

### Code Optimization

```c
// Optimized version with DMA
void optimized_adc_reading(void) {
    // Use DMA for continuous ADC conversion
    HAL_ADC_Start_DMA(&hadc1, adc_buffer, ADC_BUFFER_SIZE);
}

// Power optimization
void enter_low_power_mode(void) {
    HAL_PWR_EnterSLEEPMode(PWR_MAINREGULATOR_ON, PWR_SLEEPENTRY_WFI);
}
```

---

## Kết luận

### Tóm tắt thành quả

Dự án đã hoàn thành thành công với các tính năng:
- ✅ GPIO control và interrupt handling
- ✅ ADC reading với độ chính xác cao
- ✅ Timer-based task scheduling
- ✅ Robust error handling

### Bài học rút ra

1. **Hardware Design:** Importance of proper decoupling
2. **Software Architecture:** Modular design benefits
3. **Testing Strategy:** Unit testing saves time
4. **Documentation:** Clear documentation is crucial

### Next Steps

- Implement additional features từ roadmap
- Optimize power consumption
- Create PCB design cho production
- Develop comprehensive test suite

---

**Mã nguồn:** [GitHub Repository](https://github.com/ai-ho/project-name)

**Tài liệu tham khảo:**
- [STM32 Reference Manual](https://www.st.com)
- [HAL Library Documentation](https://www.st.com)

**Tags:** {{ page.tags | join: ", " }}
