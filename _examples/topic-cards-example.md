---
layout: topic-cards
title: "Complete Example - Topic Cards Layout"
description: "Complete example showing how to use the topic-cards layout with multiple cards, different difficulty levels, and proper metadata"
---

<div class="page-header">
    <h1 class="page-title">Embedded Systems Learning Path</h1>
    <p class="page-subtitle">From beginner concepts to advanced automotive software development - Complete guide with hands-on examples</p>
</div>

<div class="topic-cards-container">
    
    <!-- Beginner Level: IoT Monitoring System -->
    <a href="/fundamentals/iot-monitoring/" class="topic-card">
        <div class="topic-image" style="background-image: url('/fundamentals/assets/iot-monitoring-system-main.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">IoT Monitoring System với STM32</h2>
            <p class="topic-description">Xây dựng hệ thống giám sát IoT hoàn chỉnh sử dụng STM32, ESP8266, và cloud platform. Học cách kết nối sensors, truyền dữ liệu wireless, và hiển thị realtime dashboard.</p>
            <div class="topic-meta">
                <span class="topic-difficulty intermediate">Intermediate</span>
                <span class="topic-time">⏱️ 4-6 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">STM32F4</span>
                <span class="topic-tag">ESP8266</span>
                <span class="topic-tag">MQTT</span>
                <span class="topic-tag">IoT</span>
            </div>
        </div>
    </a>
    
    <!-- Beginner Level: Embedded C Programming Structure -->
    <a href="/fundamentals/prog-structure/" class="topic-card">
        <div class="topic-image" style="background-image: url('/fundamentals/assets/embedded-programming-structure.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Cấu trúc chương trình Embedded C</h2>
            <p class="topic-description">Hướng dẫn chi tiết về cách tổ chức code trong embedded systems. Từ project structure, header files, đến memory management và optimization techniques.</p>
            <div class="topic-meta">
                <span class="topic-difficulty beginner">Beginner</span>
                <span class="topic-time">⏱️ 2-3 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">Embedded C</span>
                <span class="topic-tag">Code Structure</span>
                <span class="topic-tag">Best Practices</span>
            </div>
        </div>
    </a>
    
    <!-- Advanced Level: AUTOSAR Introduction -->
    <a href="/automotive/autosar-intro/" class="topic-card">
        <div class="topic-image" style="background-image: url('/automotive/assets/autosar-architecture.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">AUTOSAR Architecture Overview</h2>
            <p class="topic-description">Giới thiệu về AUTOSAR standard trong automotive software development. Tìm hiểu về layered architecture, SWCs, RTE, và BSW stack.</p>
            <div class="topic-meta">
                <span class="topic-difficulty advanced">Advanced</span>
                <span class="topic-time">⏱️ 6-8 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">AUTOSAR</span>
                <span class="topic-tag">Automotive</span>
                <span class="topic-tag">Software Architecture</span>
            </div>
        </div>
    </a>
    
    <!-- Beginner Level: STM32 Development Kit -->
    <a href="/kits/stm32-discovery/" class="topic-card">
        <div class="topic-image" style="background-image: url('/kits/assets/stm32f407-discovery.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">STM32F407 Discovery Kit Setup</h2>
            <p class="topic-description">Hướng dẫn setup và sử dụng STM32F407 Discovery board. Từ cài đặt development environment đến các project examples và debugging techniques.</p>
            <div class="topic-meta">
                <span class="topic-difficulty beginner">Beginner</span>
                <span class="topic-time">⏱️ 1-2 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">STM32</span>
                <span class="topic-tag">Development Kit</span>
                <span class="topic-tag">Setup Guide</span>
            </div>
        </div>
    </a>
    
    <!-- Intermediate Level: CAN Bus Communication -->
    <a href="/automotive/can-bus/" class="topic-card">
        <div class="topic-image" style="background-image: url('/automotive/assets/can-bus-network.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">CAN Bus Communication Protocol</h2>
            <p class="topic-description">Deep dive vào CAN bus protocol được sử dụng rộng rãi trong automotive systems. Học về frame structure, arbitration, error handling, và practical implementation.</p>
            <div class="topic-meta">
                <span class="topic-difficulty intermediate">Intermediate</span>
                <span class="topic-time">⏱️ 3-4 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">CAN Bus</span>
                <span class="topic-tag">Communication</span>
                <span class="topic-tag">Automotive</span>
                <span class="topic-tag">Protocol</span>
            </div>
        </div>
    </a>
    
    <!-- Advanced Level: Real-time Operating Systems -->
    <a href="/fundamentals/rtos/" class="topic-card">
        <div class="topic-image" style="background-image: url('/fundamentals/assets/freertos-tasks.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Real-time Operating Systems (RTOS)</h2>
            <p class="topic-description">Tìm hiểu về RTOS concepts và practical implementation với FreeRTOS. Covers tasks, scheduling, synchronization, và memory management trong embedded systems.</p>
            <div class="topic-meta">
                <span class="topic-difficulty advanced">Advanced</span>
                <span class="topic-time">⏱️ 8-10 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">RTOS</span>
                <span class="topic-tag">FreeRTOS</span>
                <span class="topic-tag">Multitasking</span>
                <span class="topic-tag">Real-time</span>
            </div>
        </div>
    </a>

</div>

---

## 📖 How to Use This Topic Cards Template

### Step 1: Create a Page with Topic Cards Layout

Create a new markdown file and use the `topic-cards` layout:

```yaml
---
layout: topic-cards
title: "Your Page Title"
description: "Page description for SEO and meta tags"
---
```

### Step 2: Add Page Header (Optional)

```html
<div class="page-header">
    <h1 class="page-title">Your Main Title</h1>
    <p class="page-subtitle">Subtitle or description explaining the page content</p>
</div>
```

### Step 3: Create Topic Cards Container

```html
<div class="topic-cards-container">
    <!-- Your topic cards go here -->
</div>
```

### Step 4: Add Individual Topic Cards

Use this template for each topic card:

```html
<a href="/path/to/your/topic/" class="topic-card">
    <div class="topic-image" style="background-image: url('/path/to/image.png');"></div>
    <div class="topic-content">
        <h2 class="topic-title">Your Topic Title</h2>
        <p class="topic-description">Brief description of the topic content that will be truncated after 2 lines...</p>
        <div class="topic-meta">
            <span class="topic-difficulty beginner">Difficulty Level</span>
            <span class="topic-time">⏱️ Time estimate</span>
        </div>
        <div class="topic-tags">
            <span class="topic-tag">Tag1</span>
            <span class="topic-tag">Tag2</span>
            <span class="topic-tag">Tag3</span>
        </div>
    </div>
</a>
```

### Difficulty Levels Available:

- **`beginner`** - Green background (#c6f6d5)
- **`intermediate`** - Orange background (#fed7a1)  
- **`advanced`** - Red background (#fed7d7)

### Image Guidelines:

- **Size**: Square images work best (minimum 120x120px)
- **Format**: PNG, JPG, or SVG
- **Optimization**: Compress images for web to improve loading speed
- **Style**: Use `background-image` CSS property for proper scaling

### Responsive Behavior:

- **Desktop**: Horizontal layout (image left, content right)
- **Tablet**: Same as desktop but slightly smaller
- **Mobile**: Stacked layout (image on top, content below)

### Tips for Best Results:

1. **Keep descriptions concise** - They'll be truncated after 2 lines
2. **Use meaningful tags** - Help users understand the content quickly  
3. **Estimate time realistically** - Help users plan their learning
4. **Choose appropriate difficulty** - Guide users to suitable content
5. **Use high-quality images** - Make your topics visually appealing

### Example Topics Structure:

```
/fundamentals/
├── intro/               (Beginner topic)
├── prog-structure/      (Beginner/Intermediate)
├── iot-monitoring/      (Intermediate topic)
└── rtos/               (Advanced topic)

/automotive/
├── autosar-intro/      (Advanced topic)
└── can-bus/           (Intermediate topic)

/kits/
└── stm32-discovery/   (Beginner topic)
```

This template is perfect for creating overview pages, learning paths, or any collection of related topics that you want to present in an organized, visually appealing way.
