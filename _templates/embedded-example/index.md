---
layout: default
title: "Xây dựng hệ thống IoT monitoring với STM32 và WiFi"
description: "Hướng dẫn chi tiết cách xây dựng hệ thống giám sát IoT sử dụng STM32, ESP8266, và cloud platform"
date: 2025-08-03
categories: [embedded, iot, stm32, wifi]
tags: [stm32f4, esp8266, mqtt, iot, sensors, cloud]
author: Hồ Thiện Ái
image: /embedded/assets/iot-monitoring-system-main.png
featured_image: /embedded/assets/iot-monitoring-featured.jpg
difficulty: intermediate
estimated_time: "4-6 giờ"
components:
  - STM32F407VGT6 Discovery Board
  - ESP8266 WiFi Module
  - DHT22 Temperature/Humidity Sensor
  - BMP180 Pressure Sensor
  - 0.96" OLED Display (SSD1306)
  - Breadboard và Jumper wires
  - External 3.3V Power Supply
tools:
  - STM32CubeIDE
  - ST-Link Debugger
  - Arduino IDE (cho ESP8266)
  - MQTT Explorer
  - ThingSpeak hoặc AWS IoT Core
---

{% include_relative README.md %}
