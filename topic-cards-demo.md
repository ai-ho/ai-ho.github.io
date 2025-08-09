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
    <a href="/fundamentals/intro/" class="topic-card">
        <div class="topic-image" style="background-image: url('/assets/Embedded.jpg');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Introduction to Embedded Programming</h2>
            <p class="topic-description">Learn the fundamentals of embedded systems programming with C language. Perfect starting point for beginners who want to understand microcontroller programming.</p>
            <div class="topic-meta">
                <span class="topic-difficulty beginner">Beginner</span>
                <span class="topic-time">⏱️ 2-3 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">C Programming</span>
                <span class="topic-tag">Microcontrollers</span>
                <span class="topic-tag">Basics</span>
            </div>
        </div>
    </a>
    
    <!-- Example: Automotive Software -->
    <a href="/automotive/intro/" class="topic-card">
        <div class="topic-image" style="background-image: url('/automotive/assets/automotive.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Automotive Software Development</h2>
            <p class="topic-description">Advanced automotive embedded systems programming including AUTOSAR, CAN communication, and safety-critical software development standards.</p>
            <div class="topic-meta">
                <span class="topic-difficulty advanced">Advanced</span>
                <span class="topic-time">⏱️ 8-10 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">AUTOSAR</span>
                <span class="topic-tag">CAN Bus</span>
                <span class="topic-tag">Safety Critical</span>
            </div>
        </div>
    </a>
    
    <!-- Example: Development Boards -->
    <a href="/boards/" class="topic-card">
        <div class="topic-image" style="background-image: url('/boards/assets/stm32f103.png');"></div>
        <div class="topic-content">
            <h2 class="topic-title">Development Boards & Tools</h2>
            <p class="topic-description">Explore popular development boards, debuggers, and tools for embedded programming. Hands-on tutorials with STM32 and debugging tools.</p>
            <div class="topic-meta">
                <span class="topic-difficulty beginner">Beginner</span>
                <span class="topic-time">⏱️ 1-2 hours</span>
            </div>
            <div class="topic-tags">
                <span class="topic-tag">STM32</span>
                <span class="topic-tag">Hardware</span>
                <span class="topic-tag">Debugging</span>
            </div>
        </div>
    </a>

</div>

---

## 📖 Template Usage Guide

This page demonstrates the `topic-cards` layout. To create your own:

1. **Create a new page** with `layout: topic-cards`
2. **Add topic cards** using the HTML structure shown above
3. **Choose difficulty levels**: `beginner`, `intermediate`, or `advanced`
4. **Use square images** for best results (120x120px minimum)

See `/_examples/topic-cards-example.md` for complete documentation and more examples.
