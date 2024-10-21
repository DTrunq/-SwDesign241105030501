/*Đề xuất kiến trúc:
Layered Architecture (Kiến trúc phân lớp):
Presentation Layer (UI Layer): Được sử dụng cho việc nhập thông tin từ người dùng (nhân viên, quản trị viên). Giao diện sẽ chạy trên máy tính cá nhân của từng nhân viên và cho phép họ truy cập các chức năng như ghi thẻ chấm công, đặt lệnh mua hàng, và thay đổi thông tin cá nhân.
Application Layer (Business Logic Layer): Chịu trách nhiệm xử lý nghiệp vụ như tính lương, quản lý chấm công, quản lý phương thức thanh toán và tự động xử lý các kỳ trả lương. Lớp này sẽ đảm bảo tính bảo mật khi nhân viên chỉ có thể truy cập thông tin của riêng mình.
Data Access Layer (DAL): Kết nối với cơ sở dữ liệu của hệ thống để lưu trữ thông tin về nhân viên, thẻ chấm công, đơn hàng, và lương.
Integration Layer: Đảm bảo tích hợp với cơ sở dữ liệu DB2 hiện tại trên hệ thống IBM mainframe, nơi lưu trữ thông tin về các dự án và mã số tính phí.
Giải thích kiến trúc:
Layered Architecture là lựa chọn tốt cho hệ thống này vì:
Giúp phân chia trách nhiệm rõ ràng giữa các thành phần.
Đảm bảo dễ dàng bảo trì và mở rộng hệ thống khi có sự thay đổi về yêu cầu.
Cho phép tích hợp dễ dàng với các hệ thống khác như DB2.
Các thành phần chính của kiến trúc:
UI Layer: Nơi người dùng tương tác trực tiếp.
Business Logic Layer: Xử lý nghiệp vụ liên quan đến quản lý bảng lương.
Data Access Layer: Truy cập và quản lý cơ sở dữ liệu của hệ thống.
Integration Layer: Đảm bảo hệ thống mới tương tác hiệu quả với cơ sở dữ liệu DB2 cũ.
*/


![Use case diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTUVaggWbAefu9FOcLgaP92DPU2GhHhRa5EVcLgga9uVb4sK6b9PdvUSInNBHTKkLDfSMPUQd6nWaz-UcOoYbPKAIGzBeabYGgEoSbWEIGDIE98gZtpIbBJYy0MewfsCb80wKXAB4u5ArTN24hDWJWm8xEWc0k7snLqTUqm7OSk0565uY8K7bGUnGrS3gbvAQ2G10000F__0m00)
