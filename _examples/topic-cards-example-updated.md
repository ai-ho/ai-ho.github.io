---
layout: topic-cards
title: "Topic Cards Template Examples"
description: "Complete example showing how to use the topic-cards layout with multiple cards, different difficulty levels, and proper metadata"
---

<div class="page-header">
    <h1 class="page-title">Topic Cards Examples</h1>
    <p class="page-subtitle">Demonstrations of various topic card configurations</p>
</div>

<div class="topic-cards-container">
    
    <!-- IoT Monitoring System -->
    <div class="topic-card" onclick="window.location.href='/fundamentals/iot-monitoring/'">
        <div class="topic-image" style="background-image: url('/fundamentals/assets/iot-monitoring-system-main.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">IoT Monitoring System với STM32</h2>
            <div class="topic-dates">15-06-24 | 10-08-25</div>
            <p class="topic-description">Xây dựng hệ thống giám sát IoT hoàn chỉnh sử dụng STM32, ESP8266, và cloud platform. Học cách kết nối sensors, truyền dữ liệu wireless, và hiển thị realtime dashboard.</p>
            <div class="topic-tags">
                <span class="topic-tag">STM32F4</span>
                <span class="topic-tag">ESP8266</span>
                <span class="topic-tag">MQTT</span>
                <span class="topic-tag">IoT</span>
            </div>
            <a href="/fundamentals/iot-monitoring/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
    <!-- Embedded C Programming Structure -->
    <div class="topic-card" onclick="window.location.href='/fundamentals/prog-structure/'">
        <div class="topic-image" style="background-image: url('/fundamentals/assets/embedded-programming-structure.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Cấu trúc chương trình Embedded C</h2>
            <div class="topic-dates">20-04-24 | 10-08-25</div>
            <p class="topic-description">Hướng dẫn chi tiết về cách tổ chức code trong embedded systems. Từ project structure, header files, đến memory management và optimization techniques.</p>
            <div class="topic-tags">
                <span class="topic-tag">Embedded C</span>
                <span class="topic-tag">Code Structure</span>
                <span class="topic-tag">Best Practices</span>
            </div>
            <a href="/fundamentals/prog-structure/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
    <!-- AUTOSAR Introduction -->
    <div class="topic-card" onclick="window.location.href='/automotive/autosar-intro/'">
        <div class="topic-image" style="background-image: url('/automotive/assets/autosar-architecture.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">AUTOSAR Fundamental Architecture</h2>
            <div class="topic-dates">01-07-24 | 10-08-25</div>
            <p class="topic-description">Comprehensive introduction to AUTOSAR standard, layer architecture, and basic software components. Essential for automotive software development.</p>
            <div class="topic-tags">
                <span class="topic-tag">AUTOSAR</span>
                <span class="topic-tag">Automotive</span>
                <span class="topic-tag">Architecture</span>
            </div>
            <a href="/automotive/autosar-intro/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
    <!-- STM32 Discovery Board -->
    <div class="topic-card" onclick="window.location.href='/boards/stm32-discovery/'">
        <div class="topic-image" style="background-image: url('/boards/assets/stm32-discovery.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">STM32 Discovery Board Review</h2>
            <div class="topic-dates">10-08-24 | 10-08-25</div>
            <p class="topic-description">In-depth review of STM32 Discovery development board, setup guide, and hands-on examples for embedded programming.</p>
            <div class="topic-tags">
                <span class="topic-tag">STM32</span>
                <span class="topic-tag">Discovery</span>
                <span class="topic-tag">Hardware</span>
            </div>
            <a href="/boards/stm32-discovery/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
    <!-- CAN Bus Communication -->
    <div class="topic-card" onclick="window.location.href='/automotive/can-bus/'">
        <div class="topic-image" style="background-image: url('/automotive/assets/can-bus-topology.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">CAN Bus Communication Protocol</h2>
            <div class="topic-dates">25-08-24 | 10-08-25</div>
            <p class="topic-description">Complete guide to Controller Area Network (CAN) protocol implementation in automotive systems, including practical examples and troubleshooting.</p>
            <div class="topic-tags">
                <span class="topic-tag">CAN Bus</span>
                <span class="topic-tag">Communication</span>
                <span class="topic-tag">Automotive</span>
            </div>
            <a href="/automotive/can-bus/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
    <!-- Real-Time Operating Systems -->
    <div class="topic-card" onclick="window.location.href='/fundamentals/rtos/'">
        <div class="topic-image" style="background-image: url('/fundamentals/assets/rtos-concepts.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Real-Time Operating Systems (RTOS)</h2>
            <div class="topic-dates">05-09-24 | 10-08-25</div>
            <p class="topic-description">Introduction to RTOS concepts, task scheduling, inter-task communication, and practical implementation with FreeRTOS on embedded systems.</p>
            <div class="topic-tags">
                <span class="topic-tag">RTOS</span>
                <span class="topic-tag">FreeRTOS</span>
                <span class="topic-tag">Multitasking</span>
            </div>
            <a href="/fundamentals/rtos/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
</div>

---

## 📖 Template Usage Guide

This page demonstrates the correct topic-cards layout. To create your own:

1. **Create a new page** with `layout: topic-cards`
2. **Add your content** using the topic-cards-container and topic-card structure
3. **Include proper metadata**: dates, description, tags, and read-more links

### Current Template Structure:

```html
<div class="topic-cards-container">
    <div class="topic-card" onclick="window.location.href='/your-link/'">
        <div class="topic-image" style="background-image: url('/path/to/image.jpg');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Your Title</h2>
            <div class="topic-dates">DD-MM-YY | DD-MM-YY</div>
            <p class="topic-description">Your description here...</p>
            <div class="topic-tags">
                <span class="topic-tag">Tag1</span>
                <span class="topic-tag">Tag2</span>
            </div>
            <a href="/your-link/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
</div>
```

### Key Features:
- ✅ Clean div-based structure (not anchor tags)
- ✅ JavaScript click handling with onclick
- ✅ Consistent date format
- ✅ Topic tags for categorization  
- ✅ Read more links with stopPropagation
- ✅ No topic-meta (removed for simplicity)
- ✅ Responsive image scaling
- ✅ Proper semantic HTML structure

See the main pages (`/`, `/fundamentals/`, `/boards/`) for live examples.
