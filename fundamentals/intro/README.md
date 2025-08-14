## Embedded C: Ngôn ngữ C dành cho hệ thống nhúng
Ngôn ngữ C dành cho hệ thống nhúng, hay còn gọi là embedded C có gì khác biệt?

<p align="center">
  <img src="/fundamentals/intro/img/embedded-c.png" alt="Embedded C" style="width: 100vw" />
</p>

### Ngôn ngữ C
Như chúng ta đã biết, ngôn ngữ lập trình C là một ngôn ngữ lập trình cấp cao rất phổ biến. Ngôn ngữ C được xây dựng theo hướng cấu trúc, có nghĩa là các câu lệnh được thực thi một cách tuần tự theo như thiết kế của chương trình. Với cú pháp vô cùng chặt chẽ và rõ ràng, cùng với nguồn tài liệu dồi dào giúp cho các lập trình viên dễ dàng tiếp cận và học tập. 

Ngôn ngữ C được sử dụng nhiều để lập trình các hệ điều hành, drivers, hệ thống nhúng hoặc IoT. Ngày nay, với sự xuất hiện của nhiều ngôn ngữ lập trình hướng đối tượng cấp cao và hỗ trợ nhiều thư viện, ngôn ngữ C dần bị thay thế và ít phổ biến hơn. Tuy nhiên, không vì thế mà ngôn ngữ C mất đi vai trò quan trọng của mình trong các ứng dụng đòi hỏi tốc độ xử lý nhanh, điều khiển chính xác, đáp ứng thời gian thực và nguồn tài nguyên hạn chế.

### Hệ thống nhúng - embedded system
Hệ thống nhúng, nói một cách khó hiểu, là hệ thống cho phép người dùng “nhúng” chương trình của mình vào hệ thống. 

Để dễ hình dung, chúng ta có một con chip có khả năng được lập trình. Người lập trình viên sẽ viết một chương trình, sau đó biên dịch chương trình thành ngôn ngữ máy, rồi nạp chương trình này vào bộ nhớ của chip để nó thực hiện những tác vụ theo yêu cầu. Hệ thống cho phép thực hiện quy trình ở trên được gọi chung là hệ thống nhúng hay embedded system.

### Embedded C
Embedded C là một phân nhánh của ngôn ngữ lập trình C, nhưng nó có một vài điểm khác biệt. Nó được thiết dành riêng cho các hệ thống như vi điều khiển, thiết bị điện và các sản phẩm IoT.

Embedded C thừa hưởng lại gần như toàn bộ cú pháp và cấu trúc cơ bản của C, nhưng bổ sung thêm các đặc điểm giúp cho lập trình viên dễ dàng thao tác với phần cứng, nguồn tài nguyên hạn và yêu cầu thực tế của hệ thống nhúng.

### Tại sao lại chọn embedded C?
- Hiệu năng cao: Embedded C cung cấp quyền truy cập trực tiếp đến phần cứng và tối ưu hóa tài nguyên của hệ thống.
- Tốc độ thực thi nhanh:  Code C được trình biên dịch thành mã máy tương thích và hiệu quả với kiến trúc hệ thống, lệnh thực thi nhanh hơn, phù hợp với các ứng dụng cần đáp ứng thời gian thực.
- Tính linh hoạt: Cho phép lập trình viên thao tác từng bit, từng thanh của vi điều khiển trung tâm.
- Khả năng tương thích: Hầu hết các dòng vi điều khiển hiện đại và công cụ phát triển đều hỗ trợ ngôn ngữ C.

### Một số đặc điểm của embedded C
- Bit manipulation: Có khả năng đọc và ghi đến cấp độ từng bit một cách dễ dàng
- Pointer: Truy cập và thao tác trực tiếp bến vùng nhớ thông qua các tác vụ liên quan đến pointer
- Inline assemly: Có khả năng tích hợp với đoạn mã Assembly khi cần tối ưu hóa
- Interrupt handling: Xử lý ngắt hiệu quả
- Memory management: Quản lý bộ nhớ hạn chế một cách chặt chẽ

### Tổng kết
Nếu bạn đang học tập hay làm việc liên quan đến ngành điện - điện tử, cơ điện tử thì cần phải nắm rõ các khái niệm và cách sử dụng embedded C hiệu quả dành cho hệ thống nhúng. Đây là một trong những yêu cầu cơ bản để có thể đảm bảo công việc trong thị trường lao động ngày càng cạnh tranh ngày nay.
