🏠 [⬅️ Quay về trang chủ](/)

## 🔖
[🛠️ Lập trình nhúng căn bản](/embedded/) | [🚗 Phần mềm nhúng trên ô tô](/automotive/) | [💡 Kinh nghiệm làm việc](/blog/) | [🌱 Trải nghiệm cuộc sống](/blog/) | [🔌 Kit phát triển](/kits/)

## Cấu trúc chương trình Embedded C

<p align="center">
  <img src="/embedded/posts/prog_struct/img/prog_struct.png" alt="Cấu trúc chương trình Embedded C" style="width: 100vw" />
</p>

Một chương trình Embedded C thường có cấu trúc đơn giản nhưng rất chặt chẽ để đảm bảo hiệu năng và độ tin cậy khi chạy trên vi điều khiển hoặc các hệ thống nhúng. Dưới đây là các thành phần cơ bản của một chương trình Embedded C:

### 1. Khai báo thư viện và header
```c
#include <stdint.h>
#include <stdbool.h>
#include "device.h" // Header cho phần cứng cụ thể
```

### 2. Khai báo biến toàn cục và cấu hình phần cứng
```c
volatile uint8_t flag = 0;
```

### 3. Hàm khởi tạo (Init)
```c
Hàm này dùng để cấu hình các ngoại vi, thanh ghi, timer, v.v.
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
### 5. Các hàm xử lý ngoại vi, ngắt, giao tiếp
Các hàm này giúp chương trình tương tác với phần cứng và xử lý các sự kiện thực tế.

💡 Việc tổ chức chương trình rõ ràng, tách biệt các chức năng sẽ giúp mã nguồn dễ bảo trì, mở rộng và giảm thiểu lỗi khi phát triển phần mềm nhúng.

---

👉 [Danh sách các bài viết về embedded C](/embedded/posts/)

---

## 🔖
[🛠️ Lập trình nhúng căn bản](/embedded/) | [🚗 Phần mềm nhúng trên ô tô](/automotive/) | [💡 Kinh nghiệm làm việc](/blog/) | [🌱 Trải nghiệm cuộc sống](/blog/) | [🔌 Kit phát triển](/kits/)

## 🏠
🏠 [⬅️ Quay về trang chủ](/)