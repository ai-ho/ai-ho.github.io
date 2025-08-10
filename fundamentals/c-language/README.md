## Ngôn ngữ lập trình C

<p align="center">
  <img src="/fundamentals/c-language/img/c-language.png" alt="Ngôn ngữ lập trình C" style="width: 100vw" />
</p>

### Sự ra đời của ngôn ngữ C

Ngôn ngữ C phiên bản hoàn thiện chính thức được ra đời vào năm 1972 bởi Dennis Ritchie sau khi trải qua nhiều năm nghiên cứu và phát triển. Ngôn ngữ C ra đời với mục đích là để viết lại hệ điều hành UNIX thay cho assembly, đồng thời nó được thiết kế làm sao để vừa có khả năng thực thi mạnh mẽ của assembly nhưng lại vừa dễ sử dụng như ngôn ngữ bậc cao.

### Phát triển và chuẩn hóa

- **1978**: Xuất bản cuốn sách "The C Programming Language" của Brian Kernighan và Dennis Ritchie (K&R C)
- **1983**: American National Standards Institute (ANSI) bắt đầu quá trình chuẩn hóa ngôn ngữ C
- **1989**: Ra đời chuẩn ANSI C (C89/C90)
- **1999**: Chuẩn C99 với nhiều tính năng mới
- **2011**: Chuẩn C11 với cải tiến về đa luồng và bảo mật

### Đặc điểm nổi bật
- **Tính di động cao**: Code C có thể được biên dịch và chạy trên nhiều nền tảng khác nhau
- **Hiệu suất tốt**: Ngôn ngữ C được thiết kế rất gần với phần cứng, mã lệnh được tối ưu và tốc độ thực thi nhanh
- **Tối ưu hóa nguồn tài nguyên**: Ngôn ngữ C có khả năng sự dụng nguồn tài nguyên hạn chế một cách tối ưu, đáp ứng nhu cầu xây dựng một hệ thống vừa, nhỏ và tiết kiệm chi phí
- **Linh hoạt**: Cho phép lập trình viết code ở cả high level thân thiện với con người và low level thân thiện với máy tính
- **Cú pháp đơn giản**: Vì là ngôn ngữ lập trình cấp cao và nguồn tài liệu chuẩn hóa dồi dào nên C tương đối dễ học và sử dụng

### Nhược điểm

- **Quản lý bộ nhớ thủ công**: Dễ memory leak, buffer overflow, stack overflow. Việc quản lý hoàn toàn do người dùng tự giải quyết
- **Thiếu OOP**: Ngôn ngữ lập trình hướng cấu trúc nên không có sẵn tính đóng gói, kế thừa, đa hình,…
- **Thư viện hạn chế**: Thư viện chuẩn của C rất hạn chế, người dùng thường phải tự xây dựng các thư viện riêng cho ứng dụng của mình
- **An toàn thấp**: Tính an toàn (safety) khi sử dụng là rất thấp và người dùng phải tự xây dựng cơ chế kiểm tra để đảm bảo tính an toàn của chương trình.
- **Khó debug**: Runtime errors rất khó phát hiện và không có cơ chế report lỗi cho người dùng
- **Thiếu tính năng hiện đại**: Không có exception handling, phân loại theo namespace

### Ứng dụng thực tế

- **System programming**: Hệ điều hành, drivers
- **Embedded systems**: Vi điều khiển, IoT
- **Game development**: Game cần có tốc độ xử lý nhanh
- **Database systems**: MySQL, PostgreSQL
- **Compilers**: Nhiều compiler được viết bằng C

### Kết luận

Ngôn ngữ C được coi là một trong những phát minh quan trọng nhất trong lịch sử khoa học máy tính, đặt nền móng cho sự phát triển của ngành công nghệ thông tin hiện đại. C trở thành nền tảng phát triển cho nhiều ngôn ngữ khác như C++, Java, C# và được sử dụng rộng rãi trong phát triển hệ điều hành máy tính hiện đại, hệ thống nhúng, IoT.

Dù đã trải qua hơn 50 năm, cùng với sự xuất hiện và thịnh hành của nhiều ngôn ngữ lập trình cấp cao khác, nhưng ngôn ngữ C vẫn là một trong những ngôn ngữ có vai trò quan trọng và phổ biến nhất hiện nay.
