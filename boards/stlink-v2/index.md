---
layout: default
title: "ST-Link V2 Mini Debugger"
description: "Công cụ debug thiết yếu cho phát triển STM32 - Chi tiết thông số và ứng dụng"
---

<div style="text-align: center; margin-bottom: 30px;">
  <h1 style="color: #093FB4; font-weight: bold; margin-bottom: 10px;">🟣 ST-Link V2 Mini Debugger</h1>
  <p style="font-size: 18px; color: #666;">Công cụ debug chuyên nghiệp cho STM32</p>
</div>

<p align="center">
  <img src="/boards/assets/stlink_mini_debugger.png" alt="ST-Link V2 Mini Debugger" style="width: 400px; margin: 20px 0;" />
</p>

## Mô tả

Công cụ debug thiết yếu cho phát triển STM32 với khả năng lập trình trong mạch và debug thời gian thực. Công cụ chuyên nghiệp với giá cả phải chăng.

ST-Link V2 Mini là một programmer/debugger nhỏ gọn và hiệu quả, được thiết kế đặc biệt để làm việc với các vi điều khiển STM32 và STM8 của STMicroelectronics.

## Thông số kỹ thuật

### Kết nối và giao tiếp
- **Giao diện PC**: USB 2.0 Full Speed
- **Giao diện Target**: SWD (Serial Wire Debug)
- **Điện áp Target**: 1.65V đến 3.6V
- **Tốc độ SWD**: Lên đến 4MHz

### Tương thích
- **Vi điều khiển**: STM32 (tất cả series), STM8
- **IDE**: STM32CubeIDE, Keil μVision, IAR EWARM
- **Hệ điều hành**: Windows, Linux, macOS

### Đặc điểm vật lý
- **Kích thước**: Nhỏ gọn, dễ mang theo
- **Kết nối**: Cáp USB tích hợp
- **LED**: Hiển thị trạng thái hoạt động

## Tính năng nổi bật

- ✅ **Lập trình trong mạch**: Nạp firmware trực tiếp lên vi điều khiển
- ✅ **Debug thời gian thực**: Đặt breakpoint, theo dõi biến
- ✅ **Giao diện SWD**: Chỉ cần 2 dây để debug
- ✅ **Tương thích IDE**: Hoạt động với tất cả IDE phổ biến
- ✅ **Giám sát thời gian thực**: Theo dõi giá trị biến khi chạy
- ✅ **Giá cả hợp lý**: Công cụ chuyên nghiệp với giá phải chăng

## Ứng dụng

### Phát triển chuyên nghiệp
- Phát triển firmware STM32
- Debug ứng dụng phức tạp
- Kiểm tra và xác thực code

### Giáo dục và học tập
- Dạy và học lập trình nhúng
- Thực hành debug techniques
- Hiểu rõ hoạt động của vi điều khiển

### Sản xuất và kiểm tra
- Nạp firmware hàng loạt
- Kiểm tra chất lượng sản phẩm
- Cập nhật firmware

### Nghiên cứu và phát triển
- Phát triển thuật toán mới
- Tối ưu hóa hiệu năng
- Phân tích hệ thống

## Cách sử dụng ST-Link V2

### 1. Kết nối phần cứng
```
ST-Link V2    -->    STM32 Target
GND           -->    GND
SWDIO         -->    PA13 (SWDIO)
SWCLK         -->    PA14 (SWCLK)
3.3V          -->    3.3V (tùy chọn)
```

### 2. Cài đặt driver
- **Windows**: ST-Link USB driver từ STMicroelectronics
- **Linux**: Tự động nhận diện hoặc sử dụng st-link tools
- **macOS**: Homebrew hoặc manual installation

### 3. Sử dụng với STM32CubeIDE
1. Tạo project mới
2. Chọn ST-Link làm debugger
3. Build và flash code
4. Sử dụng debug features

### 4. Debug với breakpoint
```c
int main(void) {
    HAL_Init();
    SystemClock_Config();
    
    // Đặt breakpoint tại đây
    int sensor_value = read_sensor();
    
    while (1) {
        // Debug logic here
        process_data(sensor_value);
        HAL_Delay(1000);
    }
}
```

## So sánh với các công cụ khác

| Tính năng | ST-Link V2 Mini | J-Link EDU | Black Magic Probe |
|-----------|-----------------|------------|-------------------|
| Giá cả | Rẻ | Trung bình | Rẻ |
| Tốc độ debug | Tốt | Rất tốt | Tốt |
| Tương thích IDE | Rộng | Rất rộng | Hạn chế |
| Dễ sử dụng | Dễ | Trung bình | Khó |

## Troubleshooting

### Lỗi thường gặp
- **Không nhận diện thiết bị**: Kiểm tra driver và kết nối USB
- **Không kết nối được target**: Kiểm tra wiring và nguồn cấp
- **Debug chậm**: Giảm tốc độ SWD clock

### Tips sử dụng
- Luôn kết nối GND trước
- Kiểm tra điện áp target phù hợp
- Sử dụng cáp ngắn để giảm nhiễu

---

<div style="text-align: center; margin-top: 30px;">
  <a href="#" style="
    display: inline-block;
    background-color: #093FB4;
    color: white;
    padding: 12px 24px;
    text-decoration: none;
    border-radius: 5px;
    font-weight: bold;
    font-size: 16px;
    transition: background-color 0.3s;
  " onmouseover="this.style.backgroundColor='#0056b3'" onmouseout="this.style.backgroundColor='#093FB4'">
    🛒 Đặt mua ngay
  </a>
</div>
