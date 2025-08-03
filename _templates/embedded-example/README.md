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

![Sơ đồ khối hệ thống](/embedded/assets/iot-system-block-diagram.png)
*Sơ đồ khối tổng quan của hệ thống IoT monitoring*

Dự án này xây dựng một hệ thống giám sát môi trường thông minh với các tính năng:
- **Thu thập dữ liệu:** Nhiệt độ, độ ẩm, áp suất khí quyển
- **Hiển thị local:** OLED display real-time data
- **Kết nối IoT:** Gửi dữ liệu lên cloud qua WiFi
- **Monitoring dashboard:** Web interface để theo dõi từ xa

### Mục tiêu học tập

Sau khi hoàn thành dự án này, bạn sẽ:
- ✅ Hiểu được cách tích hợp multiple sensors với STM32
- ✅ Nắm vững giao tiếp I2C và UART
- ✅ Biết cách implement MQTT protocol
- ✅ Áp dụng được IoT concepts trong thực tế

### Kiến thức tiên quyết

- Lập trình C/C++ trung bình
- Hiểu biết về STM32 HAL library
- Kiến thức cơ bản về networking và IoT
- Familiar với protocol I2C, SPI, UART

---

## Yêu cầu và chuẩn bị

### Phần cứng cần thiết

![Linh kiện dự án](/embedded/assets/iot-components-layout.jpg)
*Các linh kiện cần thiết cho dự án IoT monitoring*

**Vi điều khiển và modules:**
{% for component in page.components %}
- {{ component }}
{% endfor %}

**Specifications chi tiết:**
- **STM32F407VGT6:** ARM Cortex-M4, 168MHz, 1MB Flash, 192KB RAM
- **ESP8266:** WiFi 802.11 b/g/n, TCP/IP stack, AT commands
- **DHT22:** ±0.5°C accuracy, 2-5% RH accuracy
- **BMP180:** ±0.02hPa pressure resolution

### Phần mềm và công cụ

![Môi trường phát triển](/embedded/assets/iot-development-environment.png)
*Screenshot môi trường phát triển cho IoT project*

**IDE và Tools:**
{% for tool in page.tools %}
- {{ tool }}
{% endfor %}

**Cloud Platforms:**
- ThingSpeak (free tier)
- AWS IoT Core
- Azure IoT Hub
- Google Cloud IoT

### Thiết lập workspace

```bash
# Tạo project structure
mkdir stm32_iot_monitoring
cd stm32_iot_monitoring
mkdir firmware hardware docs

# Clone libraries
git clone https://github.com/adafruit/DHT-sensor-library
git clone https://github.com/adafruit/Adafruit_SSD1306
```

---

## Thiết kế phần cứng

### Sơ đồ mạch điện

![Sơ đồ mạch chi tiết](/embedded/assets/iot-detailed-circuit-diagram.png)
*Sơ đồ mạch điện chi tiết với pin mapping*

### Bảng kết nối

| STM32 Pin | Tên Pin | Kết nối đến | Module | Mô tả chức năng |
|-----------|---------|-------------|--------|-----------------|
| PB6       | I2C1_SCL | SCL | OLED, BMP180 | I2C Clock |
| PB7       | I2C1_SDA | SDA | OLED, BMP180 | I2C Data |
| PA9       | USART1_TX | RX | ESP8266 | UART Transmit |
| PA10      | USART1_RX | TX | ESP8266 | UART Receive |
| PC0       | GPIO_Input | Data | DHT22 | Digital Data |
| PC13      | GPIO_Output | LED | Built-in LED | Status Indicator |
| 3V3       | Power | VCC | All modules | Power Supply |
| GND       | Ground | GND | All modules | Common Ground |

### Power Budget Analysis

![Power Analysis](/embedded/assets/power-consumption-analysis.png)
*Phân tích công suất tiêu thụ của hệ thống*

| Component | Operating Current | Sleep Current | Notes |
|-----------|------------------|---------------|-------|
| STM32F407 | ~50mA @ 168MHz | ~200µA (Stop mode) | Main MCU |
| ESP8266 | ~170mA (TX) | ~20µA (Deep sleep) | WiFi module |
| OLED Display | ~15mA | ~5µA (Off) | Always on display |
| Sensors | ~5mA | ~1µA | DHT22 + BMP180 |
| **Total** | **~240mA** | **~226µA** | Peak vs Sleep |

---

## Thiết lập môi trường phát triển

### Cấu hình STM32CubeIDE

![CubeIDE Configuration](/embedded/assets/cubemx-iot-config.png)
*Screenshot cấu hình project trong STM32CubeMX*

#### Bước 1: Clock Configuration

```c
// System Clock Configuration - 168MHz
void SystemClock_Config(void)
{
    RCC_OscInitTypeDef RCC_OscInitStruct = {0};
    RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};
    
    // Configure HSE oscillator
    RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_HSE;
    RCC_OscInitStruct.HSEState = RCC_HSE_ON;
    RCC_OscInitStruct.PLL.PLLState = RCC_PLL_ON;
    RCC_OscInitStruct.PLL.PLLSource = RCC_PLLSOURCE_HSE;
    RCC_OscInitStruct.PLL.PLLM = 8;
    RCC_OscInitStruct.PLL.PLLN = 336;
    RCC_OscInitStruct.PLL.PLLP = RCC_PLLP_DIV2;
    RCC_OscInitStruct.PLL.PLLQ = 7;
    
    HAL_RCC_OscConfig(&RCC_OscInitStruct);
    HAL_PWREx_EnableOverDrive();
    
    // Configure system clock
    RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK|RCC_CLOCKTYPE_SYSCLK
                                |RCC_CLOCKTYPE_PCLK1|RCC_CLOCKTYPE_PCLK2;
    RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_PLLCLK;
    RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
    RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV4;
    RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV2;
    
    HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_5);
}
```

#### Bước 2: Peripheral Configuration

![Peripheral Configuration](/embedded/assets/peripheral-config-iot.png)
*Cấu hình các peripheral trong CubeMX*

### ESP8266 AT Commands Setup

```c
// ESP8266 AT Commands for WiFi setup
const char* esp8266_commands[] = {
    "AT\r\n",                                    // Test communication
    "AT+CWMODE=1\r\n",                          // Station mode
    "AT+CWJAP=\"SSID\",\"PASSWORD\"\r\n",       // Connect to WiFi
    "AT+CIPSTART=\"TCP\",\"mqtt.broker.com\",1883\r\n", // Connect to MQTT
    "AT+CIPMODE=1\r\n",                         // Transparent mode
    "AT+CIPSEND\r\n"                            // Start sending data
};
```

---

## Lập trình firmware

### Cấu trúc project

```
firmware/
├── Core/
│   ├── Src/
│   │   ├── main.c
│   │   ├── sensors.c
│   │   ├── wifi_manager.c
│   │   ├── mqtt_client.c
│   │   ├── display.c
│   │   └── data_logger.c
│   └── Inc/
│       ├── main.h
│       ├── sensors.h
│       ├── wifi_manager.h
│       ├── mqtt_client.h
│       └── config.h
├── Drivers/
└── Middlewares/
```

### Main Application Logic

```c
// main.c - Main application loop
#include "main.h"
#include "sensors.h"
#include "wifi_manager.h"
#include "mqtt_client.h"
#include "display.h"

/* Private variables */
I2C_HandleTypeDef hi2c1;
UART_HandleTypeDef huart1;
TIM_HandleTypeDef htim2;

typedef struct {
    float temperature;
    float humidity;
    float pressure;
    uint32_t timestamp;
} SensorData_t;

SensorData_t sensorData;

int main(void)
{
    /* System initialization */
    HAL_Init();
    SystemClock_Config();
    
    /* Peripheral initialization */
    MX_GPIO_Init();
    MX_I2C1_Init();
    MX_USART1_Init();
    MX_TIM2_Init();
    
    /* Initialize modules */
    sensors_init();
    display_init();
    wifi_manager_init();
    mqtt_client_init();
    
    /* Start timer for periodic data collection */
    HAL_TIM_Base_Start_IT(&htim2);
    
    /* Main application loop */
    while (1)
    {
        /* Handle WiFi connection */
        wifi_manager_process();
        
        /* Handle MQTT communication */
        mqtt_client_process();
        
        /* Update display */
        display_update(&sensorData);
        
        /* Process commands */
        process_uart_commands();
        
        HAL_Delay(100);
    }
}
```

### Sensor Data Collection

```c
// sensors.c - Sensor data collection
#include "sensors.h"

/* DHT22 sensor functions */
HAL_StatusTypeDef DHT22_ReadData(float *temperature, float *humidity)
{
    uint8_t data[5] = {0};
    uint32_t timeout = 1000;
    
    /* Send start signal */
    HAL_GPIO_WritePin(DHT22_GPIO_Port, DHT22_Pin, GPIO_PIN_RESET);
    HAL_Delay(18);
    HAL_GPIO_WritePin(DHT22_GPIO_Port, DHT22_Pin, GPIO_PIN_SET);
    delay_us(30);
    
    /* Read response */
    if (DHT22_Read_Bit() != 0) return HAL_ERROR;
    if (DHT22_Read_Bit() != 1) return HAL_ERROR;
    
    /* Read 40 bits of data */
    for (int i = 0; i < 5; i++) {
        data[i] = DHT22_Read_Byte();
    }
    
    /* Verify checksum */
    if (data[4] != ((data[0] + data[1] + data[2] + data[3]) & 0xFF)) {
        return HAL_ERROR;
    }
    
    /* Convert to float values */
    *humidity = ((data[0] << 8) | data[1]) / 10.0f;
    *temperature = (((data[2] & 0x7F) << 8) | data[3]) / 10.0f;
    
    if (data[2] & 0x80) {
        *temperature *= -1;
    }
    
    return HAL_OK;
}

/* BMP180 pressure sensor */
HAL_StatusTypeDef BMP180_ReadPressure(float *pressure)
{
    uint8_t data[3];
    int32_t UP, UT;
    int32_t B3, B5, B6, X1, X2, X3, p;
    uint32_t B4, B7;
    
    /* Read uncompensated temperature */
    BMP180_WriteReg(0xF4, 0x2E);
    HAL_Delay(5);
    BMP180_ReadRegs(0xF6, data, 2);
    UT = (data[0] << 8) | data[1];
    
    /* Read uncompensated pressure */
    BMP180_WriteReg(0xF4, 0x34);
    HAL_Delay(5);
    BMP180_ReadRegs(0xF6, data, 3);
    UP = ((data[0] << 16) | (data[1] << 8) | data[2]) >> 8;
    
    /* Calculate compensated pressure */
    X1 = ((UT - BMP180_AC6) * BMP180_AC5) >> 15;
    X2 = (BMP180_MC << 11) / (X1 + BMP180_MD);
    B5 = X1 + X2;
    
    B6 = B5 - 4000;
    X1 = (BMP180_B2 * ((B6 * B6) >> 12)) >> 11;
    X2 = (BMP180_AC2 * B6) >> 11;
    X3 = X1 + X2;
    B3 = (((BMP180_AC1 * 4 + X3) << 1) + 2) >> 2;
    
    X1 = (BMP180_AC3 * B6) >> 13;
    X2 = (BMP180_B1 * ((B6 * B6) >> 12)) >> 16;
    X3 = ((X1 + X2) + 2) >> 2;
    B4 = (BMP180_AC4 * (uint32_t)(X3 + 32768)) >> 15;
    B7 = ((uint32_t)UP - B3) * (50000 >> 1);
    
    if (B7 < 0x80000000) {
        p = (B7 * 2) / B4;
    } else {
        p = (B7 / B4) * 2;
    }
    
    X1 = (p >> 8) * (p >> 8);
    X1 = (X1 * 3038) >> 16;
    X2 = (-7357 * p) >> 16;
    p = p + ((X1 + X2 + 3791) >> 4);
    
    *pressure = p / 100.0f; // Convert to hPa
    
    return HAL_OK;
}
```

### MQTT Communication

```c
// mqtt_client.c - MQTT protocol implementation
#include "mqtt_client.h"

typedef struct {
    char topic[64];
    char payload[256];
    uint8_t qos;
} MQTT_Message_t;

HAL_StatusTypeDef MQTT_Publish(const char* topic, const char* payload)
{
    char mqtt_command[512];
    uint16_t packet_length;
    
    /* Create MQTT PUBLISH packet */
    packet_length = snprintf(mqtt_command, sizeof(mqtt_command),
        "AT+CIPSEND=%d\r\n", 
        strlen(topic) + strlen(payload) + 10);
    
    /* Send AT command */
    HAL_UART_Transmit(&huart1, (uint8_t*)mqtt_command, 
                      packet_length, HAL_MAX_DELAY);
    
    /* Wait for ">" prompt */
    if (wait_for_response(">", 5000) != HAL_OK) {
        return HAL_ERROR;
    }
    
    /* Send MQTT packet */
    packet_length = create_mqtt_publish_packet(mqtt_command, 
                                               topic, payload);
    HAL_UART_Transmit(&huart1, (uint8_t*)mqtt_command, 
                      packet_length, HAL_MAX_DELAY);
    
    return HAL_OK;
}

void MQTT_PublishSensorData(SensorData_t *data)
{
    char json_payload[256];
    
    /* Create JSON payload */
    snprintf(json_payload, sizeof(json_payload),
        "{"
        "\"temperature\":%.1f,"
        "\"humidity\":%.1f,"
        "\"pressure\":%.1f,"
        "\"timestamp\":%lu"
        "}",
        data->temperature,
        data->humidity,
        data->pressure,
        data->timestamp
    );
    
    /* Publish to different topics */
    MQTT_Publish("sensors/temperature", json_payload);
    MQTT_Publish("sensors/environment", json_payload);
}
```

### OLED Display Interface

```c
// display.c - OLED display management
#include "display.h"
#include "ssd1306.h"

void display_update(SensorData_t *data)
{
    char buffer[32];
    
    /* Clear display */
    ssd1306_Fill(Black);
    
    /* Display title */
    ssd1306_SetCursor(2, 0);
    ssd1306_WriteString("IoT Monitor", Font_11x18, White);
    
    /* Display temperature */
    ssd1306_SetCursor(2, 20);
    snprintf(buffer, sizeof(buffer), "Temp: %.1f C", data->temperature);
    ssd1306_WriteString(buffer, Font_7x10, White);
    
    /* Display humidity */
    ssd1306_SetCursor(2, 32);
    snprintf(buffer, sizeof(buffer), "Humi: %.1f %%", data->humidity);
    ssd1306_WriteString(buffer, Font_7x10, White);
    
    /* Display pressure */
    ssd1306_SetCursor(2, 44);
    snprintf(buffer, sizeof(buffer), "Pres: %.1f hPa", data->pressure);
    ssd1306_WriteString(buffer, Font_7x10, White);
    
    /* Display connection status */
    ssd1306_SetCursor(2, 56);
    if (wifi_is_connected()) {
        ssd1306_WriteString("WiFi: Connected", Font_6x8, White);
    } else {
        ssd1306_WriteString("WiFi: Disconnected", Font_6x8, White);
    }
    
    /* Update display */
    ssd1306_UpdateScreen();
}
```

### Timer Interrupt Handler

```c
// Timer interrupt for periodic data collection
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
{
    if (htim->Instance == TIM2) {
        static uint32_t counter = 0;
        counter++;
        
        /* Collect sensor data every 10 seconds */
        if (counter % 100 == 0) {
            if (DHT22_ReadData(&sensorData.temperature, 
                              &sensorData.humidity) == HAL_OK) {
                BMP180_ReadPressure(&sensorData.pressure);
                sensorData.timestamp = HAL_GetTick();
                
                /* Publish to cloud */
                if (wifi_is_connected()) {
                    MQTT_PublishSensorData(&sensorData);
                }
                
                /* Toggle status LED */
                HAL_GPIO_TogglePin(GPIOC, GPIO_PIN_13);
            }
        }
    }
}
```

---

## Testing và Debug

### Unit Testing Framework

![Debug Session](/embedded/assets/iot-debug-session.png)
*Screenshot debug session trong STM32CubeIDE*

#### Test Cases Implementation

```c
// test_sensors.c - Unit tests for sensors
typedef enum {
    TEST_PASS,
    TEST_FAIL,
    TEST_TIMEOUT
} TestResult_t;

TestResult_t test_dht22_communication(void)
{
    float temp, humi;
    uint32_t start_time = HAL_GetTick();
    
    /* Test DHT22 data read */
    HAL_StatusTypeDef result = DHT22_ReadData(&temp, &humi);
    
    if (result != HAL_OK) {
        printf("❌ DHT22 communication failed\n");
        return TEST_FAIL;
    }
    
    /* Validate data ranges */
    if (temp < -40.0f || temp > 80.0f) {
        printf("❌ DHT22 temperature out of range: %.1f°C\n", temp);
        return TEST_FAIL;
    }
    
    if (humi < 0.0f || humi > 100.0f) {
        printf("❌ DHT22 humidity out of range: %.1f%%\n", humi);
        return TEST_FAIL;
    }
    
    printf("✅ DHT22 test passed - T:%.1f°C H:%.1f%%\n", temp, humi);
    return TEST_PASS;
}

TestResult_t test_wifi_connection(void)
{
    printf("Testing WiFi connection...\n");
    
    /* Send AT command */
    send_at_command("AT\r\n");
    if (wait_for_response("OK", 2000) != HAL_OK) {
        printf("❌ ESP8266 not responding\n");
        return TEST_FAIL;
    }
    
    /* Test WiFi connection */
    send_at_command("AT+CWJAP?\r\n");
    if (wait_for_response("+CWJAP:", 5000) != HAL_OK) {
        printf("❌ WiFi not connected\n");
        return TEST_FAIL;
    }
    
    printf("✅ WiFi connection test passed\n");
    return TEST_PASS;
}
```

### Integration Testing

![System Integration Test](/embedded/assets/integration-test-setup.jpg)
*Setup cho integration testing với oscilloscope và logic analyzer*

#### Performance Monitoring

```c
// performance_monitor.c - System performance monitoring
typedef struct {
    uint32_t sensor_read_time;
    uint32_t mqtt_publish_time;
    uint32_t display_update_time;
    uint32_t total_cycle_time;
    uint32_t heap_usage;
    uint32_t stack_usage;
} PerformanceMetrics_t;

void monitor_performance(void)
{
    static PerformanceMetrics_t metrics;
    uint32_t start_time, end_time;
    
    /* Measure sensor reading time */
    start_time = DWT_CYCCNT;
    DHT22_ReadData(&sensorData.temperature, &sensorData.humidity);
    BMP180_ReadPressure(&sensorData.pressure);
    end_time = DWT_CYCCNT;
    metrics.sensor_read_time = (end_time - start_time) / (SystemCoreClock / 1000000);
    
    /* Measure MQTT publish time */
    start_time = DWT_CYCCNT;
    MQTT_PublishSensorData(&sensorData);
    end_time = DWT_CYCCNT;
    metrics.mqtt_publish_time = (end_time - start_time) / (SystemCoreClock / 1000000);
    
    /* Print performance metrics */
    printf("Performance Metrics:\n");
    printf("  Sensor Read: %lu μs\n", metrics.sensor_read_time);
    printf("  MQTT Publish: %lu μs\n", metrics.mqtt_publish_time);
    printf("  Heap Usage: %lu bytes\n", get_heap_usage());
    printf("  Stack Usage: %lu bytes\n", get_stack_usage());
}
```

---

## Kết quả và demo

### Cloud Dashboard

![ThingSpeak Dashboard](/embedded/assets/thingspeak-dashboard.png)
*Dashboard trên ThingSpeak hiển thị real-time sensor data*

### Mobile App Interface

![Mobile App](/embedded/assets/mobile-app-interface.jpg)
*Giao diện mobile app để monitoring từ xa*

### Performance Metrics

| Metric | Target | Achieved | Status |
|--------|--------|----------|--------|
| Data Update Rate | 30s | 10s | ✅ Exceeded |
| WiFi Connection Time | <30s | 15s | ✅ Passed |
| Sensor Accuracy | ±1°C | ±0.5°C | ✅ Passed |
| Power Consumption | <300mA | 240mA | ✅ Passed |
| Memory Usage | <80% | 65% | ✅ Passed |

### Video Demo

[🎥 **Live Demo Video**](https://youtube.com/iot-monitoring-demo)
*Click để xem video demo hoạt động real-time của hệ thống*

---

## Troubleshooting

### Common Issues Flowchart

![Troubleshooting Guide](/embedded/assets/iot-troubleshooting-flowchart.png)
*Flowchart hướng dẫn troubleshooting*

| Vấn đề | Triệu chứng | Nguyên nhân có thể | Giải pháp |
|--------|-------------|-------------------|-----------|
| DHT22 không đọc được | Data = 0xFF | Timing issues, wiring | Check connections, adjust timing |
| ESP8266 không kết nối WiFi | AT commands timeout | Power supply, antenna | Check 3.3V supply, AT firmware |
| MQTT data không gửi được | No data on broker | Network, credentials | Verify broker settings, auth |
| OLED display blank | No display output | I2C address, power | Check I2C scan, supply voltage |
| System hang/reset | Watchdog trigger | Stack overflow, infinite loop | Enable debug, check stack usage |

### Debug Utilities

```c
// debug_utils.c - Debugging utilities
void debug_print_system_info(void)
{
    printf("\n=== System Information ===\n");
    printf("MCU: STM32F407VGT6\n");
    printf("Clock: %lu MHz\n", SystemCoreClock / 1000000);
    printf("Flash: %lu KB\n", FLASH_SIZE);
    printf("RAM: %lu KB\n", RAM_SIZE);
    printf("Uptime: %lu seconds\n", HAL_GetTick() / 1000);
    
    printf("\n=== Peripheral Status ===\n");
    printf("I2C1: %s\n", (hi2c1.State == HAL_I2C_STATE_READY) ? "Ready" : "Busy");
    printf("UART1: %s\n", (huart1.gState == HAL_UART_STATE_READY) ? "Ready" : "Busy");
    printf("Timer2: %s\n", (htim2.State == HAL_TIM_STATE_READY) ? "Ready" : "Error");
    
    printf("\n=== Network Status ===\n");
    printf("WiFi: %s\n", wifi_is_connected() ? "Connected" : "Disconnected");
    printf("MQTT: %s\n", mqtt_is_connected() ? "Connected" : "Disconnected");
    printf("IP Address: %s\n", get_ip_address());
}

void debug_dump_sensor_data(void)
{
    printf("\n=== Sensor Raw Data ===\n");
    printf("DHT22 Raw: [0x%02X, 0x%02X, 0x%02X, 0x%02X, 0x%02X]\n",
           dht22_raw_data[0], dht22_raw_data[1], dht22_raw_data[2],
           dht22_raw_data[3], dht22_raw_data[4]);
    printf("BMP180 UT: %ld, UP: %ld\n", bmp180_ut, bmp180_up);
    printf("Calculated Values:\n");
    printf("  Temperature: %.2f°C\n", sensorData.temperature);
    printf("  Humidity: %.2f%%\n", sensorData.humidity);
    printf("  Pressure: %.2f hPa\n", sensorData.pressure);
}
```

---

## Phát triển thêm

### Feature Roadmap

![Feature Development Roadmap](/embedded/assets/iot-feature-roadmap.png)
*Roadmap phát triển các tính năng mở rộng*

#### Phase 1: Advanced Sensing ✅
- [x] Temperature, Humidity, Pressure monitoring
- [x] Real-time OLED display
- [x] Cloud data logging
- [x] Mobile dashboard

#### Phase 2: Smart Features 🚧
- [ ] Machine Learning for anomaly detection
- [ ] Predictive maintenance alerts
- [ ] Multi-location deployment
- [ ] Historical data analysis

#### Phase 3: Enterprise Integration 📋
- [ ] REST API development
- [ ] Database integration (InfluxDB)
- [ ] Grafana dashboards
- [ ] Email/SMS notifications
- [ ] Industrial protocols (Modbus, OPC-UA)

### Code Optimization Examples

```c
// power_management.c - Advanced power optimization
void enter_low_power_mode(void)
{
    /* Disable unnecessary peripherals */
    __HAL_RCC_GPIOB_CLK_DISABLE();
    __HAL_RCC_GPIOD_CLK_DISABLE();
    
    /* Configure wake-up sources */
    HAL_PWR_EnableWakeUpPin(PWR_WAKEUP_PIN1);
    
    /* Enter Stop Mode */
    HAL_PWR_EnterSTOPMode(PWR_LOWPOWERREGULATOR_ON, PWR_STOPENTRY_WFI);
    
    /* Re-initialize system after wake-up */
    SystemClock_Config();
    MX_GPIO_Init();
}

// edge_computing.c - Local data processing
typedef struct {
    float min_temp;
    float max_temp;
    float avg_temp;
    uint32_t sample_count;
} TempStatistics_t;

void process_local_analytics(void)
{
    static TempStatistics_t stats = {0};
    static float temp_buffer[100];
    static uint8_t buffer_index = 0;
    
    /* Add new sample */
    temp_buffer[buffer_index] = sensorData.temperature;
    buffer_index = (buffer_index + 1) % 100;
    
    /* Calculate statistics */
    calculate_statistics(temp_buffer, 100, &stats);
    
    /* Detect anomalies */
    if (detect_temperature_anomaly(&stats)) {
        send_alert("Temperature anomaly detected!");
    }
    
    /* Send processed data instead of raw data */
    publish_analytics_data(&stats);
}
```

---

## Kết luận

### Tóm tắt thành quả

Dự án IoT monitoring system đã hoàn thành thành công với các tính năng:
- ✅ Multi-sensor data collection (DHT22, BMP180)
- ✅ Real-time local display trên OLED
- ✅ WiFi connectivity với ESP8266
- ✅ MQTT protocol implementation
- ✅ Cloud dashboard integration
- ✅ Robust error handling và diagnostics

### Bài học rút ra

1. **System Integration:** Tầm quan trọng của timing và synchronization
2. **Power Management:** Cân bằng giữa performance và power consumption
3. **Communication Protocols:** MQTT reliability và QoS considerations
4. **Error Handling:** Robust firmware design cho production environment
5. **Testing Strategy:** Importance của comprehensive testing framework

### Technical Achievements

| Aspect | Achievement | Industry Standard |
|--------|-------------|------------------|
| Real-time Performance | 10s update rate | ✅ Meets IoT requirements |
| Power Efficiency | 240mA average | ✅ Suitable for battery operation |
| Communication Reliability | 99.5% uptime | ✅ Enterprise grade |
| Code Quality | 85% test coverage | ✅ Production ready |

### Next Steps

- **Scalability:** Deploy multiple nodes cho wide-area monitoring
- **AI Integration:** Implement predictive analytics
- **Security:** Add encryption và authentication
- **Certification:** Pursue CE/FCC compliance cho commercial deployment

Dự án này đã cung cấp kiến thức solid foundation về IoT development, từ embedded programming đến cloud integration, và có thể serve như base cho các projects phức tạp hơn trong tương lai.

---

**Mã nguồn:** [GitHub Repository](https://github.com/ai-ho/stm32-iot-monitoring)

**Tài liệu tham khảo:**
- [STM32F4 Reference Manual](https://www.st.com/resource/en/reference_manual/dm00031020.pdf)
- [ESP8266 AT Commands Guide](https://www.espressif.com/sites/default/files/documentation/4a-esp8266_at_instruction_set_en.pdf)
- [MQTT Protocol Specification](http://docs.oasis-open.org/mqtt/mqtt/v3.1.1/mqtt-v3.1.1.html)
- [ThingSpeak IoT Platform](https://thingspeak.com/docs)

**Tags:** {{ page.tags | join: ", " }}

---

> 💡 **Note:** Đây là một example template để minh họa cách viết embedded project post với STM32 và IoT. Khi sử dụng, hãy thay thế nội dung với dự án thực tế của bạn.
