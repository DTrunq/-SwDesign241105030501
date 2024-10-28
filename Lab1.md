### 1. Phân tích kiến trúc
 Đề xuất kiến trúc
Hệ thống Payroll System sẽ được thiết kế theo kiến trúc phân lớp (Layered Architecture), bao gồm các lớp chính như sau:
- **Application Layer**: Chứa các thành phần cụ thể của ứng dụng, bao gồm giao diện người dùng (UI) cho phép nhân viên nhập thông tin và truy xuất báo cáo.
- **Business Services Layer**: Chứa các thành phần logic nghiệp vụ, xử lý thông tin như tính toán lương, xử lý timecard và purchase order.
- **Data Access Layer**: Chứa các thành phần để truy cập dữ liệu từ các cơ sở dữ liệu, bao gồm cả việc truy cập thông tin từ Project Management Database.
Ý nghĩa của từng thành phần trong kiến trúc
- **Application Layer**: Đảm bảo rằng người dùng có thể tương tác với hệ thống một cách dễ dàng và hiệu quả. Nó cũng cho phép mở rộng tính năng trong tương lai.
- **Business Services Layer**: Xử lý logic nghiệp vụ quan trọng, giúp tách biệt quy trình xử lý và giảm thiểu sự phụ thuộc giữa các thành phần.
- **Data Access Layer**: Đảm bảo tính an toàn và bảo mật dữ liệu, cho phép truy cập đến các cơ sở dữ liệu mà không cần thay đổi logic nghiệp vụ.
  
 Biểu đồ package mô tả kiến trúc

![Default Diagram](https://www.planttext.com/api/plantuml/png/R9112i8m44NtESNGaxJYHb0GgYlfOam7YIPfIQP2aPxCXKVo2YRQghNERdZ_puEvNs-fPtJS62rgb2Sy42HhR5sbDUIjPp89N0I4UUEihhMIoAgoiCIMt928izikYkVIYN5hrdXboNl8oPsL9F-dsulxHF416sL8eYkd95GCMHw1N_KS6I6JCjgdqaZtwEaL-3xjgYD9Ng4DLw9aI0wMJgHao_2w1m000F__0m00)
### 2.Cơ chế phân tích
Đề xuất các cơ chế
- Quản lý Timecard: Nhân viên có thể nhập và chỉnh sửa thông tin timecard của họ.
- Tính toán Lương: Hệ thống tự động tính toán lương dựa trên thời gian làm việc và doanh số bán hàng.
- Chọn Phương thức Thanh toán: Nhân viên có thể chọn phương thức nhận lương (gửi qua bưu điện, chuyển khoản ngân hàng, hoặc nhận tại văn phòng).
- Báo cáo: Cung cấp khả năng tạo báo cáo cho nhân viên về giờ làm việc, tổng tiền lương đã nhận, và thời gian nghỉ còn lại.
### 3.Phân tích ca sử dụng Payment
Các lớp phân tích 
- Employee: Lớp đại diện cho nhân viên với thông tin như mã nhân viên, tên, và phương thức thanh toán.
- Paycheck: Lớp ghi nhận thông tin lương cho từng kỳ thanh toán, bao gồm số tiền và ngày thanh toán.
- BankSystem: Lớp xử lý giao dịch thanh toán qua ngân hàng, gửi thông tin và nhận xác nhận.
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/R8_D3S8m38Nldi8BT84UK0NYNi44bZ4YQlD3uXuoMm-Cn0eaGWGgSNtl-vxiv_eOabBKnSv0h3xYqORPPn489JPi0Zd5aJBVXATDk2StdNDIiG0V2xjTWx77azmNIOg1iXMdqAg2VVK2Zj6pfDJ0dxBRJXwykvfe_qmMhftHLwNso6-Ur7W7WxXBVVK5003__mC0)
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/P951JiCm44NtFeML5I2rebilK46mO052wWacpgYDQe-3FKQAgfwi2ux45R1974ZmmjPyV_dz6NzTFhU1mNEqHcW38SWdsndN8ygJa7dXM3ytIkxOjxGVT0ABSwM3tYBn2_B1BSmUtoC6VXiSLzTAVhYs4MSnGjE5Fg0-5cWtraieM1U9bMnSh0tEi8_0AK_U1tcFX3vLvUd_q0UWuwuFZBPWwwJSQvqPhz7MwETqza01DBUEbi4wxpI6K1ei-TNKMQBNpXa4oW6c8LURIgvMihfThs-gtp6eANwGTsAIYpiTVyAhGlynRv6Q_9lV0000__y30000)

Giải thích biểu đồ lớp

- Employee: Thông tin và yêu cầu thanh toán của nhân viên.
- Paycheck: Ghi nhận thông tin thanh toán cho mỗi nhân viên.
- BankSystem: Xử lý các giao dịch thanh toán qua ngân hàng.
### 4. Phân tích ca sử dụng Maintain Timecard
Các lớp phân tích
- Employee: Ghi nhận thời gian làm việc và gửi thông tin lên hệ thống.
- Timecard: Lưu trữ thông tin thời gian làm việc của nhân viên.

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9hRa5EVcLgAbS1K3WpERCWCQz48IGpDpKviIY5YmichQ1h1nUrKYWkJShDB87nDJIvO4oGCfWMAuNa_BoqpABSn9BC_3oW8eVKl1IGnG00003__mC0)

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9hRa5EVcLgga8rbm88f4BvdYbM2i4bHPbvwH3nlCJSL5IHujAatCoIaCpSrEJ4eXGDJIk5ilpC5AvQBgZ9C1cOoILGFhh9AOabG9DTW2I4dv5VMbGSdb-KdGfKc99VcfG3bKZEI2nAJ_KhpKrABO8R0RGExWKbGoK5NLq59GCzFIqbXFrMKASMAzXnEQJcfO0y3m000F__0m00)

Giải thích biểu đồ lớp
- Employee: Thông tin và hành động của nhân viên liên quan đến việc ghi nhận thời gian làm việc.
- Timecard: Thông tin chi tiết về thời gian làm việc của nhân viên cho các dự án
