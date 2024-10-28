1. Phân tích kiến trúc:
- Dựa trên yêu cầu, chúng ta sẽ áp dụng kiến trúc Three-Tier Architecture với các lớp chính:
- Application Layer: Giao diện desktop Windows cho nhân viên để nhập thông tin chấm công, tạo đơn mua hàng, chọn phương thức thanh toán, và xem báo cáo.
- Business Services Layer: Xử lý logic nghiệp vụ, bao gồm tính toán lương, xử lý chấm công, và quản lý đơn hàng.
- Data Access Layer: Quản lý truy xuất và tương tác với cơ sở dữ liệu, bao gồm một cơ chế đặc biệt để giao tiếp với Project Management Database (cơ sở dữ liệu DB2 cũ trên IBM mainframe).
Giải thích các thành phần trong kiến trúc
- Employee: Lưu trữ thông tin cơ bản và lịch sử làm việc của nhân viên.
- Timecard: Lưu thông tin chấm công của nhân viên cho mỗi ngày làm việc và dự án tương ứng (charge number).
- Paycheck: Chứa dữ liệu về mức lương, các khoản phụ cấp, và phương thức thanh toán của nhân viên.
- BankSystem: Gửi yêu cầu chuyển khoản đến tài khoản ngân hàng của nhân viên nếu chọn phương thức chuyển khoản.
- ProjectManagementDatabase: Cơ sở dữ liệu cũ chứa thông tin các dự án và mã charge, được sử dụng để xác định thời gian và công sức phân bổ cho các dự án.
![Default Diagram](https://www.planttext.com/api/plantuml/png/V991RiCW44Ntd09bdqtNaHL7xg9I8qTfBZ21KKkB0GtGo8foiYnwf5wXfd6H4yTTylWpy-V3z_bhwGDGY8rcp87uW5Vaiz8vhGG4PGr_XXPfne-CSw71U_xOE6rRn2VZOiXqYyvIM5iPDMQuWRP14sgNEdbs6enOHQyCTfeNf4ybq8y7TTLajUu56UzKWm98tlABWrlQM_Z3GmiL1E2b4Cd5v9PLMOyc3rdV_mf54c_WiIQ9b2w6GpTatr44lWRJdLCfJpxsdVvgzulir-9YKQqUYYArkVSoSsaFPbvCHygcmywruopOlNoo_hyr65kYaUb7_G000F__0m00)
2. Cơ chế phân tích
-Đề xuất các cơ chế cần giải quyết
-Dựa trên yêu cầu, các cơ chế phân tích chính bao gồm:
-Persistence (Lưu trữ): Cần lưu trữ thông tin nhân viên, bảng chấm công, phiếu lương và đơn mua hàng để đảm bảo khả năng truy cập và kiểm tra dữ liệu khi cần.
-Security (Bảo mật): Bảo vệ dữ liệu nhạy cảm như thông tin phiếu lương, số tài khoản ngân hàng, và thông tin cá nhân.
-Legacy Interface (Giao diện Hệ thống Cũ): Giao tiếp với cơ sở dữ liệu Project Management Database mà không cập nhật nó, chỉ đọc thông tin các dự án và mã charge.
-Scheduling (Lập lịch): Thiết lập lịch trình tự động để hệ thống có thể tạo phiếu lương vào mỗi thứ Sáu và ngày làm việc cuối cùng của tháng.
