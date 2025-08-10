---
layout: default
title: "STM32F103 Blue Pill"
description: "Board phát triển ARM Cortex-M3 phổ biến - Chi tiết thông số và ứng dụng"
---

<div style="text-align: center; margin-bottom: 30px;">
  <h1 style="color: #093FB4; font-weight: bold; margin-bottom: 10px;">🔵 STM32F103 Blue Pill</h1>
  <p style="font-size: 18px; color: #666;">Board phát triển ARM Cortex-M3 phổ biến</p>
</div>

<p align="center">
  <img src="/boards/assets/stm32f103.png" alt="STM32F103 Blue Pill Board" style="width: 400px; margin: 20px 0;" />
</p>

## Mô tả

Board phát triển ARM Cortex-M3 phổ biến với CPU 72MHz, 64KB Flash và nhiều tùy chọn GPIO. Hoàn hảo cho việc học lập trình nhúng và các dự án IoT.

STM32F103 Blue Pill là một trong những board phát triển phổ biến nhất trong cộng đồng maker và kỹ sư nhúng nhờ vào sự kết hợp hoàn hảo giữa hiệu năng cao và giá thành hợp lý.

## Thông số kỹ thuật

### Vi điều khiển
- **CPU**: ARM Cortex-M3, 72MHz
- **Flash Memory**: 64KB
- **RAM**: 20KB
- **Package**: LQFP48

### GPIO và giao tiếp
- **GPIO**: 37 chân có thể lập trình
- **UART**: 3 kênh (USART1, USART2, USART3)
- **SPI**: 2 kênh (SPI1, SPI2)
- **I2C**: 2 kênh (I2C1, I2C2)
- **CAN**: 1 kênh
- **PWM**: Nhiều kênh với timer

### Nguồn cấp
- **Điện áp hoạt động**: 3.3V
- **Nguồn cấp**: 5V qua USB hoặc VIN pin
- **Tiêu thụ**: Thấp, hỗ trợ các chế độ sleep

## Tính năng nổi bật

- ✅ **Hiệu năng cao**: ARM Cortex-M3 72MHz
- ✅ **Tương thích Arduino IDE**: Dễ dàng lập trình
- ✅ **Nhiều giao tiếp**: UART, SPI, I2C, CAN, PWM
- ✅ **Giá thành hợp lý**: Phù hợp cho học tập và nguyên mẫu
- ✅ **Cộng đồng lớn**: Nhiều tài liệu và hỗ trợ
- ✅ **Kích thước nhỏ gọn**: Dễ tích hợp vào dự án

## Ứng dụng

### Học tập và giáo dục
- Học lập trình ARM Cortex-M
- Thực hành lập trình nhúng
- Các khóa học vi điều khiển

### Dự án IoT
- Cảm biến nhiệt độ, độ ẩm
- Điều khiển thiết bị từ xa
- Thu thập và truyền dữ liệu

### Điều khiển động cơ
- Điều khiển servo motor
- Điều khiển stepper motor
- Hệ thống tự động hóa

### Giao tiếp và kết nối
- Thực hiện các giao thức truyền thông
- Gateway cho các hệ thống
- Cầu nối giữa các thiết bị

## Bắt đầu với STM32F103

### 1. Cài đặt môi trường phát triển
- **Arduino IDE**: Dễ sử dụng cho người mới bắt đầu
- **STM32CubeIDE**: Môi trường chuyên nghiệp từ ST
- **PlatformIO**: Hỗ trợ nhiều framework

### 2. Lập trình đầu tiên
```c
// Blink LED đơn giản
void setup() {
  pinMode(PC13, OUTPUT);  // LED built-in
}

void loop() {
  digitalWrite(PC13, HIGH);
  delay(1000);
  digitalWrite(PC13, LOW);
  delay(1000);
}
```

### 3. Tài liệu tham khảo
- [STM32F103 Datasheet](https://www.st.com/resource/en/datasheet/stm32f103c8.pdf)
- [Reference Manual](https://www.st.com/resource/en/reference_manual/cd00171190-stm32f101xx-stm32f102xx-stm32f103xx-stm32f105xx-and-stm32f107xx-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)
- [Arduino STM32 Wiki](https://github.com/stm32duino/wiki/wiki)

---

<div style="text-align: center; margin-top: 30px;">
  <div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
    <a href="#" style="
      display: inline-block;
      background-color: #EE4D2D;
      color: white;
      padding: 12px 24px;
      text-decoration: none;
      border-radius: 5px;
      font-weight: bold;
      font-size: 16px;
      transition: background-color 0.3s;
      min-width: 150px;
    " onmouseover="this.style.backgroundColor='#d73211'" onmouseout="this.style.backgroundColor='#EE4D2D'">
      🛒 Mua trên Shopee
    </a>
    
    <a href="#" style="
      display: inline-block;
      background-color: #000000;
      color: white;
      padding: 12px 24px;
      text-decoration: none;
      border-radius: 5px;
      font-weight: bold;
      font-size: 16px;
      transition: background-color 0.3s;
      min-width: 150px;
    " onmouseover="this.style.backgroundColor='#333333'" onmouseout="this.style.backgroundColor='#000000'">
      🎵 Mua trên TikTok
    </a>
  </div>
</div>
