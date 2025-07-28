## Cấu trúc chương trình Embedded C

<p align="center">
  <img src="/embedded/program-structure/img/prog_struct.png" alt="Cấu trúc chương trình Embedded C" style="width: 100vw" />
</p>

Một chương trình Embedded C thường có cấu trúc đơn giản nhưng rất chặt chẽ để đảm bảo hiệu năng và độ tin cậy khi chạy trên vi điều khiển hoặc các hệ thống nhúng. Dưới đây là các thành phần cơ bản của một chương trình Embedded C:

### 1. Khai báo thư viện và header
```c
#include <stdint.h>
#include <stdbool.h>
#include "device.h" // Header cho phần cứng cụ thể
```

### 2. Khai báo biến toàn cục và cấu hình phần cứng
#### 2.1. Khai báo biến toàn cục
```c
volatile uint8_t flag = 0;
```
#### 2.2. Cấu hình phần cứng (Hardware Configuration)
Các bước cấu hình phần cứng thường bao gồm thiết lập các chân GPIO, cấu hình các ngoại vi như UART, SPI, I2C, Timer, ADC... để chuẩn bị cho việc vận hành chương trình.

```c
void Hardware_Config(void) {
    // Thiết lập chân GPIO làm output
    GPIO_InitTypeDef GPIO_InitStruct = {0};
    GPIO_InitStruct.Pin = GPIO_PIN_0;
    GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
    HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

    // Cấu hình UART, Timer, ADC... nếu cần
}
```

### 3. Hàm khởi tạo (Init)
Hàm này dùng để cấu hình các ngoại vi, thanh ghi, timer, v.v.
```c
void System_Init(void) {
    // Cấu hình GPIO, UART, Timer, ...
}
```

### 4. Hàm main
Đây là điểm bắt đầu của chương trình, thường chứa vòng lặp vô hạn để xử lý các tác vụ.
```c
int main(void) {
    System_Init();
    while(1) {
        // Xử lý chính của chương trình
    }
}
```
#### Giải thích về vòng lặp `while(1) or while(true)`
Trong các chương trình Embedded C, vòng lặp `while(1) or while(true)` (hay còn gọi là vòng lặp vô hạn) là một thành phần rất quan trọng. Khi chương trình bắt đầu chạy, sau khi thực hiện các bước khởi tạo, nó sẽ đi vào vòng lặp này và liên tục thực hiện các tác vụ chính cho đến khi thiết bị bị tắt nguồn hoặc reset.

- Vòng lặp này đảm bảo chương trình luôn hoạt động, liên tục kiểm tra và xử lý các sự kiện như đọc cảm biến, điều khiển thiết bị, xử lý giao tiếp, v.v.
- Trong vòng lặp, bạn có thể gọi các hàm xử lý, kiểm tra trạng thái, hoặc phản hồi các tín hiệu từ phần cứng.
- Đây là đặc trưng của phần mềm nhúng, vì thiết bị thường không có hệ điều hành hoặc không cần thoát chương trình như trên máy tính cá nhân.

### 5. Các hàm xử lý ngoại vi, ngắt, giao tiếp
Các hàm này giúp chương trình tương tác với phần cứng và xử lý các sự kiện thực tế.
#### Ví dụ về hàm xử lý ngắt (Interrupt Handler)
```c
// Hàm xử lý ngắt Timer
void TIM1_IRQHandler(void) {
    if (TIM1->SR & TIM_SR_UIF) { // Kiểm tra cờ ngắt
        TIM1->SR &= ~TIM_SR_UIF; // Xóa cờ ngắt
        // Thực hiện tác vụ khi có ngắt timer
        flag = 1;
    }
}
```

💡 Việc tổ chức chương trình rõ ràng, tách biệt các chức năng sẽ giúp mã nguồn dễ bảo trì, mở rộng và giảm thiểu lỗi khi phát triển phần mềm nhúng.

---

👉 [Danh sách các bài viết về embedded C](/embedded/posts/)