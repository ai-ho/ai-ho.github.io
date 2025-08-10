---
layout: topic-cards
title: "Topic Cards Demo"
description: "Demo page showing the topic-cards layout with examples"
permalink: /topic-cards-demo/
---

<div class="page-header">
    <h1 class="page-title">Topic Cards Layout Demo</h1>
    <p class="page-subtitle">Example of how to create beautiful topic overview pages</p>
</div>

<div class="topic-cards-container">
    
    <!-- Example: Embedded Programming -->
    <div class="topic-card" onclick="window.location.href='/fundamentals/intro/'">
        <div class="topic-image" style="background-image: url('/assets/Embedded.jpg');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Introduction to Embedded Programming</h2>
            <div class="topic-dates">15-03-24 | 10-08-25</div>
            <p class="topic-description">Learn the fundamentals of embedded systems programming with C language. Perfect starting point for beginners who want to understand microcontroller programming.</p>
            <div class="topic-tags">
                <span class="topic-tag">C Programming</span>
                <span class="topic-tag">Microcontrollers</span>
                <span class="topic-tag">Basics</span>
            </div>
            <a href="/fundamentals/intro/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
    <!-- Example: Automotive Software -->
    <div class="topic-card" onclick="window.location.href='/automotive/intro/'">
        <div class="topic-image" style="background-image: url('/automotive/assets/automotive.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Automotive Software Development</h2>
            <div class="topic-dates">10-05-24 | 10-08-25</div>
            <p class="topic-description">Advanced automotive embedded systems programming including AUTOSAR, CAN communication, and safety-critical software development standards.</p>
            <div class="topic-tags">
                <span class="topic-tag">AUTOSAR</span>
                <span class="topic-tag">CAN Bus</span>
                <span class="topic-tag">Safety Critical</span>
            </div>
            <a href="/automotive/intro/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>
    
    <!-- Example: Development Boards -->
    <div class="topic-card" onclick="window.location.href='/boards/'">
        <div class="topic-image" style="background-image: url('/boards/assets/stm32f103.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Development Boards & Tools</h2>
            <div class="topic-dates">15-07-24 | 10-08-25</div>
            <p class="topic-description">Explore popular development boards, debuggers, and tools for embedded programming. Hands-on tutorials with STM32 and debugging tools.</p>
            <div class="topic-tags">
                <span class="topic-tag">STM32</span>
                <span class="topic-tag">Hardware</span>
                <span class="topic-tag">Debugging</span>
            </div>
            <a href="/boards/" class="topic-read-more" onclick="event.stopPropagation();">Đọc thêm >></a>
        </div>
    </div>

</div>

---

## 📖 Template Usage Guide

This page demonstrates the `topic-cards` layout. To create your own:

1. **Create a new page** with `layout: topic-cards`
2. **Add topic cards** using the HTML structure shown above
3. **Choose difficulty levels**: `beginner`, `intermediate`, or `advanced`
4. **Use square images** for best results (120x120px minimum)

See `/_examples/topic-cards-example.md` for complete documentation and more examples.
