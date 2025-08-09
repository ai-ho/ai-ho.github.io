# Templates Folder

Thư mục này chứa các template (mẫu) và examples để tạo nhanh các bài viết mới cho blog và embedded projects.

## 📁 Cấu trúc thư mục

```
_templates/
├── README.md                          # Hướng dẫn sử dụng templates
├── blog-post-template.md              # Template cơ bản cho blog posts
├── embedded-post-template.md          # Template cơ bản cho embedded projects
├── blog-example/                      # Ví dụ blog post hoàn chỉnh
│   └── index.md                       # "Embedded Systems trong ngành Ô tô"
└── embedded-example/                  # Ví dụ embedded project hoàn chỉnh
    └── index.md                       # "IoT Monitoring System với STM32"
```

## 🎯 Cách sử dụng

### 1. Templates cơ bản

#### Blog Post Template (`blog-post-template.md`)
- **Sử dụng cho:** Các bài viết blog thông thường, chia sẻ kiến thức, kinh nghiệm
- **Cách dùng:** Copy template → Rename → Đặt vào `/blog/posts/` → Chỉnh sửa nội dung

#### Embedded Post Template (`embedded-post-template.md`)  
- **Sử dụng cho:** Các dự án embedded, hướng dẫn lập trình vi điều khiển
- **Cách dùng:** Copy template → Rename → Đặt vào `/fundamentals/posts/` → Chỉnh sửa nội dung

### 2. Examples hoàn chỉnh

#### Blog Example (`blog-example/index.md`)
- **Chủ đề:** "Tìm hiểu về Embedded Systems trong ngành Ô tô"
- **Nội dung:** Blog post hoàn chỉnh về automotive embedded systems
- **Mục đích:** Tham khảo structure và style cho technical blog posts

#### Embedded Example (`embedded-example/index.md`)
- **Chủ đề:** "Xây dựng hệ thống IoT monitoring với STM32 và WiFi"
- **Nội dung:** Project hoàn chỉnh từ hardware design đến cloud integration
- **Mục đích:** Reference cho complex embedded projects

## 📝 Quy trình tạo bài viết mới

### Cho Blog Posts:
1. **Copy template hoặc example:** 
   ```bash
   cp _templates/blog-example/index.md blog/posts/2025-08-03-your-title.md
   ```
2. **Chỉnh sửa front matter:** title, description, date, tags
3. **Thay thế nội dung:** Giữ structure, thay đổi content
4. **Thêm images:** Đặt vào `/blog/assets/`
5. **Preview và publish**

### Cho Embedded Projects:
1. **Copy example project:**
   ```bash
   cp _templates/embedded-example/index.md embedded/posts/2025-08-03-project-name.md
   ```
2. **Cập nhật specifications:** components, tools, difficulty
3. **Customize content:** Hardware design, code examples, testing
4. **Add technical images:** Circuit diagrams, screenshots, results
5. **Test và deploy**

## Cấu trúc Template được cập nhật

### Blog Post Template - Các phần chính:

1. **Header với hình ảnh chủ đề chính**
2. **Mục lục (Table of Contents)** - Tự động linking
3. **Giới thiệu với mục tiêu bài viết**
4. **Tổng quan chủ đề** - Với hình ảnh overview
5. **Phần 1: Khái niệm cơ bản** - Definitions, principles, classifications
6. **Phần 2: Ứng dụng thực tế** - Industry applications, daily life usage
7. **Phần 3: Ví dụ minh họa** - Case studies với code examples
8. **Phần 4: Best Practices** - Do's, Don'ts, Tips & Tricks
9. **Kết luận** - Summary và references

### Embedded Post Template - Các phần chính:

1. **Header với hình ảnh dự án chính**
2. **Mục lục chi tiết** - 10 sections chính
3. **Tổng quan dự án** - System block diagram, learning objectives
4. **Yêu cầu và chuẩn bị** - Components, tools, workspace setup
5. **Thiết kế phần cứng** - Circuit diagrams, pin mapping, PCB layout
6. **Thiết lập môi trường phát triển** - IDE configuration, project structure
7. **Lập trình firmware** - Initialization, GPIO, application logic, interrupts
8. **Testing và Debug** - Unit testing, integration testing, performance
9. **Kết quả và demo** - Videos, screenshots, metrics
10. **Troubleshooting** - Common issues, debug tips
11. **Phát triển thêm** - Feature roadmap, optimization
12. **Kết luận** - Summary, lessons learned, next steps

## Hình ảnh Templates

### Các loại hình ảnh cần chuẩn bị:

#### Cho Blog Posts:
- `your-topic-main-image.png` - Hình ảnh chủ đề chính (1200x630px)
- `your-topic-featured-image.jpg` - Featured image cho social sharing
- `topic-overview.png` - Sơ đồ tổng quan chủ đề
- `working-principle.png` - Minh họa nguyên lý hoạt động
- `industrial-application.jpg` - Ứng dụng trong công nghiệp
- `case-study-1.png` - Hình ảnh case study
- `tips-and-tricks.png` - Infographic tips hữu ích

#### Cho Embedded Projects:
- `your-project-main-image.png` - Hình ảnh tổng quan dự án (1200x630px)
- `your-project-featured.jpg` - Featured image
- `system-block-diagram.png` - Sơ đồ khối hệ thống
- `components-layout.jpg` - Layout các linh kiện
- `development-environment.png` - Screenshot môi trường phát triển
- `detailed-circuit-diagram.png` - Sơ đồ mạch chi tiết
- `pcb-layout.png` - Layout PCB (nếu có)
- `cubeide-config.png` - Cấu hình IDE
- `clock-config.png` - Clock configuration
- `pin-config.png` - Pin configuration
- `gpio-setup-code.png` - Screenshot code GPIO
- `debug-session.png` - Debug session
- `oscilloscope-measurement.jpg` - Đo tín hiệu
- `demo-setup.jpg` - Setup demo
- `result-1.png` - Screenshot kết quả
- `result-2.jpg` - Hình ảnh thực tế
- `troubleshooting-flowchart.png` - Flowchart troubleshooting
- `feature-roadmap.png` - Roadmap tính năng

## Kích thước hình ảnh khuyến nghị:

- **Main images:** 1200x630px (optimal for social sharing)
- **Diagrams:** 800x600px hoặc 1024x768px
- **Screenshots:** Full resolution, crop phần cần thiết
- **Code screenshots:** Đủ rõ để đọc code
- **Circuit diagrams:** High resolution, clear labels
- **Photos:** Ít nhất 1024px width, good lighting

## Cấu trúc Front Matter

### Các trường bắt buộc:
- `layout`: luôn là "default"
- `title`: tiêu đề bài viết
- `description`: mô tả ngắn cho SEO
- `date`: ngày đăng (YYYY-MM-DD)
- `author`: tên tác giả

### Các trường tùy chọn:
- `categories`: danh mục bài viết
- `tags`: từ khóa
- `image`: hình ảnh đại diện
- `difficulty`: độ khó (chỉ cho embedded)
- `components`: linh kiện cần thiết (chỉ cho embedded)
- `tools`: công cụ cần thiết (chỉ cho embedded)

## Tips

1. **Hình ảnh:** Đặt hình ảnh trong thư mục `assets` tương ứng
2. **SEO:** Viết `description` hấp dẫn và có từ khóa
3. **Tags:** Sử dụng tags phù hợp để dễ tìm kiếm
4. **Code:** Sử dụng syntax highlighting với ngôn ngữ phù hợp
5. **Liên kết:** Thêm tài liệu tham khảo và mã nguồn

## Ví dụ cấu trúc thư mục

```
/blog/posts/
├── 2025-08-01-gioi-thieu-ve-embedded-systems.md
├── 2025-08-02-hoc-lap-trinh-c-cho-vi-dieu-khien.md
└── assets/
    ├── embedded-systems-overview.png
    └── c-programming-basics.jpg

/fundamentals/posts/
├── 2025-08-01-led-blink-arduino.md
├── 2025-08-02-uart-communication-stm32.md
└── assets/
    ├── arduino-led-circuit.png
    └── stm32-uart-diagram.jpg
```
