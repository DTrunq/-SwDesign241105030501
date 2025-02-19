# Phân tích ca sử dụng: Create Administrative Report

## 1. Mô tả ngắn gọn
Ca sử dụng **Create Administrative Report** cho phép **Payroll Administrator** tạo các báo cáo quản trị dựa trên các tiêu chí cụ thể như giờ làm việc hoặc tổng thu nhập năm của nhân viên.

## 2. Xác định các lớp

### Boundary Classes (Lớp giao diện):
- **PaymentSelectionUI**: Giao diện cho phép người dùng chọn hình thức thanh toán và cung cấp các tiêu chí báo cáo.

### Control Classes (Lớp điều khiển):
- **PaymentController**: Lớp điều khiển xử lý logic khi người dùng chọn các hình thức thanh toán và khởi tạo báo cáo.

### Entity Classes (Lớp thực thể):
- **PaymentMethod**: Quản lý các phương thức thanh toán.
- **Employee**: Quản lý thông tin về nhân viên, liên kết thông tin thanh toán với từng nhân viên cụ thể.
- **Payment**: Chứa thông tin chi tiết về thanh toán như tiền lương và hình thức thanh toán.

## 3. Biểu đồ tuần tự
Biểu đồ tuần tự minh họa luồng tương tác giữa các lớp khi Payroll Administrator yêu cầu tạo và lưu báo cáo quản trị.
![](https://www.planttext.com/api/plantuml/png/Z9HDRi8m48NtFiM85KZq0YmgeY1LxA947C2D1x3asAbja7AsBdgaNg7-YObfWsWMLZJppPkPvoZVdrzROwcsbquGsbgbeQA3La8KhEEI6wkf3r83LK5w1_AMzrHQMDJOAsrh_BYWiOVzmZE7_HnJAccz9Ee0rUKSrA2-yXOZqSmHCKL8LS3BgskrWR4vM0MjHceHT239OU-HgfYGc70OjwWvXQKTUbm32qLKdjmxThrG0-8gwr1fTUKCVvUF3Ufo0mrAzYTTbo7TpAVXw1mTOoUKw2pcIfAw2KKRU8knMzTtQf21afb-ag_HNhHCAfXQ9QtoHgHuENcNnSD4Z9jUq24pRnSZgPXGOLqSshDI1esttT0hWZtVZ0VtpDvF0CTcIqaxvxTGRLXy5Qf-EPhpEie4B7CsLqnQQ_3QKN7q8A7Jb66U7bj-vCwnL9hNk2dSHtlakWifKCTKwkTYsIH-pQVevEY8tYCe37hNt0MqL3FpsD1T9FBavDjzye5hCmfFTnxd-k_Uz_Z3tIVCtJVPkiF_Wtu0003__mC0)
## 4. Hành vi của từng lớp

### Payroll Administrator (PA)
- Yêu cầu hệ thống tạo báo cáo.
- Cung cấp các tiêu chí như loại báo cáo, ngày bắt đầu/kết thúc, tên nhân viên.
- Quyết định lưu hoặc không lưu báo cáo.

### ReportRequestUI (UI)
- Hiển thị biểu mẫu để PA nhập tiêu chí.
- Gửi tiêu chí đến `ReportController`.
- Hiển thị báo cáo và yêu cầu thông tin lưu trữ từ PA nếu cần.

### ReportController (RC)
- Gửi tiêu chí đến `ReportService` để tạo báo cáo.
- Trả báo cáo về cho UI để hiển thị.
- Xử lý yêu cầu lưu báo cáo từ UI.

### ReportService (RS)
- Tạo báo cáo dựa trên tiêu chí đã nhận.
- Lưu báo cáo nếu có yêu cầu.

### Report (R)
- Tạo báo cáo dựa trên tiêu chí.
- Trả kết quả lại cho `ReportService`.

---

## 5. Biểu đồ lớp

### Các lớp phân tích và nhiệm vụ:

#### AdminReportUI
- **Nhiệm vụ**: Lớp giao diện cho người dùng nhập tiêu chí và lưu báo cáo.

#### AdminReportController
- **Nhiệm vụ**: Xử lý logic tạo báo cáo và lưu trữ.

#### Report
- **Nhiệm vụ**: Tạo báo cáo dựa trên các tiêu chí đã nhận.

#### ReportCriteria
- **Nhiệm vụ**: Lớp này lưu trữ các tiêu chí tạo báo cáo, chẳng hạn như loại báo cáo, ngày bắt đầu và kết thúc.

#### Project
- **Nhiệm vụ**: Quản lý mã dự án và các thông tin liên quan.

#### Employee
- **Nhiệm vụ**: Quản lý thông tin nhân viên và tạo báo cáo liên quan đến nhân viên.

---

### Quan hệ giữa các lớp:

1. `AdminReportUI` tương tác với `AdminReportController` để gửi yêu cầu tạo báo cáo.
2. `AdminReportController` lấy dữ liệu từ `Report`, `Project`, và `Employee` để tạo báo cáo dựa trên `ReportCriteria`.

## Biểu đồ lớp phân tích
![](https://www.planttext.com/api/plantuml/png/X9EnJiCm48PtFyLjj58hCNT0hGf2I0X1WGTmtLDYIEpWs4W5CQ0EdPcP2ggGAY74IWQ6y29v0bu19t5AAQLai7MMVtzt_rq-a_TshAdI9Wn8VCv5H1KDWGKqZZjQAzut6lUO5CVy2c6Ja0tefXC6GPRSH-1nAc70isGiI261pY3aeeUHLFfq3wu9v9-70XNLM9xNwkLfJ2-haq0oghaKBJYsIE7LoSqIwUFEKcuDdFjs7wsWTQNGIWO1geggyC9Wh1s2AQvHSTe2Tz_5lvDHnLRTQy3_oMa_IrvPiOrSPgLusO2gT0_rDjMqLZorAAYoSi9ccSl9CC8oBbfbfIv4CIY2-Ik7IfuXM-3gha-LXmScxAEA5u4xOHJ88U8VJVecLtKtO4vlGRusmF7BqFboPAW0wyJOJaUMl51WSwF8p-beDhTMTx05krdop66OpWomxEt9aDMTpb_ekNRjPs_J8Gmi4e9y8jTfd4sLA4mVS-4hf1EnHbKvje85mayV15poT2R8KYiNa-mQuUKLJUtGyA8wFtqcf6sDp7_0Bm000F__0m00)
# Phân tích ca sử dụng: Create Employee Report

## 1. Mô tả ngắn gọn
Nhân viên có thể tạo các loại báo cáo như "Tổng giờ làm việc," "Tổng giờ làm việc cho một dự án," "Nghỉ phép/Bệnh," hoặc "Tổng lương đến hiện tại trong năm." Báo cáo này có thể được lưu lại nếu nhân viên yêu cầu.

## 2. Các lớp phân tích:
- **Boundary Class**: `ReportUI`
- **Control Class**: `ReportController`
- **Entity Class**: `Report`
- **Entity Class**: `Project`

## 3. Biểu đồ tuần tự
![Biểu đồ tuần tự](https://www.planttext.com/api/plantuml/png/Z5JDZjCm4BxxAKOzB-BU0rffGS0540LndjeJhNSTJnXFYl9i77WaNW4xZTjGqf8UglnyFpFVZFFxvw_xf2ZQjy6aPnz1E951gopmfkq23qHcptrqA0Dyfev5lxutbgCAX-d1m_4ka1YAwhK2wzqduIUoQanLX1UlJbfRs9K2OFCWX4edrmcmCHLOIFNbjcYsdKAJwvGH05QyadYyuf891--eedNew0x6ti5btpkWwCOhWq4dteW2ds3pXHK3lEDU4dnZUIOtMcFjRMCW_-QbNaQppK--zvGKy80-u3uGT4SoM7QKPWfdLb6QB8g0YgV34c_2N3FMNk9AjtDYhttg0WuBl2jpf51WS_YAL7ObzpHISwX_aVCRiu9yEV_hNMtXBKMIicOJAGySOOyfMtEybBYPvapWXkCynxfvV3vPoq5-xDJdQZ8muQ6MEgxb2MyVEH_KL37_vBnuK1gVTovYIu0vji0MYy-DYTOpSuEuRkLdVS0Fhu-ZsCi5eUMfxMRqSMAbxOwiRpmjrhDSJRvklBHLgHJbLfo33wo-6SuHSGEfjvPIQlfmZ9z2cdsv7EV9HDR_ZMOIhetvP55SBgdi_Nt-An_bFm000F__0m00)

## 4. Nhiệm vụ của từng lớp

### Employee (Nhân viên)
- Tương tác với giao diện người dùng để khởi tạo yêu cầu tạo báo cáo, cung cấp các tiêu chí cho báo cáo, và chọn lưu báo cáo nếu cần.

### ReportUI (Lớp giao diện người dùng)
- Thu thập thông tin tiêu chí báo cáo từ nhân viên, bao gồm loại báo cáo, ngày bắt đầu, ngày kết thúc và mã dự án (nếu cần).
- Hiển thị báo cáo cho nhân viên và cung cấp tùy chọn lưu báo cáo.
- Xác nhận tên và vị trí lưu báo cáo khi nhân viên chọn lưu.

### ReportController (Lớp điều phối)
- Xử lý và điều phối quy trình tạo báo cáo.
- Gửi yêu cầu đến lớp Project để lấy danh sách mã dự án nếu loại báo cáo cần mã dự án.
- Gửi yêu cầu đến lớp Report để tạo báo cáo dựa trên tiêu chí được cung cấp và lưu trữ báo cáo nếu nhân viên chọn lưu.

### Project (Lớp thực thể dự án)
- Cung cấp danh sách mã dự án từ Cơ sở Dữ liệu Quản lý Dự án, để hỗ trợ việc tạo báo cáo "Total Hours Worked for a Project".

### Report (Lớp thực thể báo cáo)
- Tạo dữ liệu báo cáo dựa trên tiêu chí được cung cấp từ ReportController.
- Lưu báo cáo đến tên và vị trí được chỉ định khi ReportController yêu cầu lưu.

## 5. Biểu đồ lớp

### a) Các lớp phân tích và nhiệm vụ của từng lớp

#### Employee
- Nhiệm vụ: Lớp này đại diện cho nhân viên, cho phép truy xuất và quản lý thông tin về nhân viên.
- Thuộc tính:
  - `employeeID`
  - `name`
  - `position`
- Phương thức:
  - `getEmployeeInfo()`: Lấy thông tin nhân viên cho báo cáo.

#### ReportGenerator
- Nhiệm vụ: Xử lý yêu cầu từ người dùng để tạo các loại báo cáo khác nhau.
- Thuộc tính:
  - `reportType`
  - `startDate`
  - `endDate`
- Phương thức:
  - `generateReport()`: Tạo báo cáo dựa trên tiêu chí được cung cấp.
  - `selectChargeNumber()`: Lựa chọn mã phí cho báo cáo dự án cụ thể.

#### EmployeeReportUI
- Nhiệm vụ: Giao diện cho phép người dùng chọn loại báo cáo, nhập tiêu chí, và yêu cầu lưu báo cáo.
- Thuộc tính:
  - `selectedReportType`
  - `inputCriteria`
- Phương thức:
  - `displayReportOptions()`: Hiển thị các lựa chọn loại báo cáo.
  - `enterCriteria()`: Yêu cầu người dùng nhập tiêu chí báo cáo.
  - `displayReport()`: Hiển thị báo cáo đã tạo cho người dùng.

#### FileManager
- Nhiệm vụ: Xử lý lưu trữ và xóa các báo cáo đã tạo.
- Thuộc tính:
  - `fileName`
  - `filePath`
- Phương thức:
  - `saveReport()`: Lưu báo cáo vào hệ thống.
  - `discardReport()`: Xóa báo cáo không lưu.

### b) Quan hệ giữa các lớp
- `EmployeeReportUI` tương tác với `ReportGenerator` để yêu cầu tạo báo cáo và lấy thông tin liên quan từ `Employee`.
- `ReportGenerator` có thể yêu cầu `Employee` cung cấp thông tin nhân viên nếu cần thiết cho báo cáo.
- `ReportGenerator` sau khi tạo báo cáo sẽ gửi kết quả tới `EmployeeReportUI` để hiển thị.
- `FileManager` được `EmployeeReportUI` sử dụng để lưu hoặc xóa báo cáo sau khi người dùng xác nhận.

### c) Biểu đồ lớp
![Biểu đồ lớp](https://www.planttext.com/api/plantuml/png/T5BBJiCm4BpxAto4GyGz1rIf1PG31HNuW2NP9XQ9RRoReWZnPHpu97u1Eo-eKtA8el7EpcGytvzVAs9mt3Qre1UbfJE48g-1I5urjZOTedmNqZ-9n178DgbKcaTKGuEfV62dT3b2rf1YPVGHB6M9FEtCzDwSdQVoO5GXFiIek4Dh7D-WHWTit2piUlonix5Gxtq3xF7mddpg8iA2ThyK1ubPUZWah37dTGMkn6tRFADRUfkS3mkUijdSGCPYzvz9fMtBQwSOdO8eaaAHhQ4Rk7SsX4QHETIUED6ZioFwqlErgl4MD9Juc-NUOzlbbGNu7hYA_14SJaVcbNDmnL9vaLEIN2ukjk-F_ywPv9lYIiG3WJJtB_K5U6sH_70132U7__vgsjkcYz4ZZVqHOkMR4Ph-0m00__y30000)

# Phân tích ca sử dụng Maintain Employee Information 
1. Mô tả ngắn gọn

Ca sử dụng "Maintain Employee Information" cho phép Payroll Administrator (Quản trị viên Lương) thực hiện các thao tác duy trì thông tin nhân viên như: thêm mới, cập nhật, và xóa. Payroll Administrator sẽ chọn hành động muốn thực hiện (thêm, cập nhật, hoặc xóa). Hệ thống sẽ hướng dẫn để nhập thông tin cần thiết, xác nhận và lưu lại thông tin.

2. Các lớp phân tích
  - Actor: PayrollAdministrator
  - Boundary class: EmployeeUI 
  - Control Class: EmployeeController 
  - Entity Class: Employee 

3. Biều đồ tuần tự
![](https://www.planttext.com/api/plantuml/png/x5N1Ji904BtlLqmyIQ9-00S34MCua1W97x1qXxXnkrkdKqc_pOEVv2yu2uM2hL28YHT9QCgoxysRzwRTp_UFGSwQk4YTob-i1mevAfrm87ZK9GNdXYQrtkPCMXRLF1JUQ2hXFirSA15dOvK4px9pktIt_ksG57gsN6zMgeqKhcztwFemZOhWOgAjP_bk_uEnNmHADTlWBrIDYFWstZuyKaWp1a61z2Gmk1mQSmMpp6Z6AnYXGyPUDrMoD-6AHodj68GBTArFWNnEb8MRtWnAhovVSNIHS-yPct2uz3gLnhZCv8gStFHQL3M3YkrvqwwckNkNemztX68cU5pMUC8aaDc3_rJu0JrI9DY2nwCETQC78vjdJfVxfR-X3-KmVGxB1bYXox6Qa5zBjn9rHh2jxRJv-8Il1UPS8wqyBJ0lkzaPyKmMtt2Ve5E40Yt87m0UZx29xU9LbTB1iJqoyiMAuipH_rx_XB6N-uMbjAfVJTtwVVG_TNyoTIlladKigpEcitcRB4sCRmCyxjqUh7QWasyJJI-r_AXyMrmENQFKGAxnLFy2003__mC0)
4. Nhiệm Vụ của Từng Lớp

PayrollAdministrator (Quản trị viên Lương)
  - Tương tác với giao diện người dùng để thêm, cập nhật, hoặc xóa thông tin nhân viên.
  - Nhập thông tin nhân viên mới, xác nhận việc xóa nhân viên, và thực hiện các chỉnh sửa cần thiết.

EmployeeUI (Lớp giao diện người dùng)
  - Hiển thị các lựa chọn thao tác (Thêm, Cập nhật, Xóa) cho Payroll Administrator.
  -Nhận thông tin nhân viên từ Payroll Administrator để thêm mới hoặc cập nhật.
  - Xác nhận thao tác xóa nhân viên với Payroll Administrator.
  - Hiển thị ID nhân viên mới hoặc thông tin cập nhật cho Payroll Administrator.

EmployeeController (Lớp điều khiển)
  - Xử lý và điều phối yêu cầu thêm, cập nhật, hoặc xóa thông tin nhân viên từ EmployeeUI.
  - Gửi yêu cầu tới lớp Employee để tạo, truy xuất, cập nhật, hoặc đánh dấu nhân viên cần xóa.
  - Truyền thông tin hoặc xác nhận về trạng thái nhân viên đến EmployeeUI.

Employee (Lớp thực thể nhân viên)
  - Tạo và lưu trữ thông tin nhân viên mới, bao gồm việc sinh mã ID độc nhất.
  - Truy xuất thông tin nhân viên để hiển thị cho Payroll Administrator trong quá trình cập nhật hoặc xóa.
  - Cập nhật các chi tiết nhân viên khi cần.
  - Đánh dấu nhân viên cần xóa để hệ thống trả lương cuối cùng trước khi xóa khỏi hệ thống.
5. Biểu đồ lớp
a)  Các lớp phân tích và nhiệm vụ của từng lớp

PayrollAdministrator
  - Nhiệm vụ: Đại diện cho người sử dụng chính, người thực hiện các thao tác duy trì thông tin nhân viên.
  - Thuộc tính:
    + administratorID
    + name
  - Phương thức:
    + selectFunction(): Chọn chức năng (thêm, cập nhật, hoặc xóa).

EmployeeManager
  - Nhiệm vụ: Xử lý các thao tác thêm, cập nhật và xóa thông tin nhân viên.
  - Thuộc tính:
    + employeeList
  - Phương thức:
    + addEmployee(): Thêm nhân viên mới.
    + updateEmployee(): Cập nhật thông tin nhân viên.
    + deleteEmployee(): Xóa thông tin nhân viên.

Employee
  - Nhiệm vụ: Đại diện cho thông tin nhân viên trong hệ thống.
  - Thuộc tính:
    + employeeID
    + name
    + employeeType (giờ, lương, hoặc hoa hồng)
    + address
    + socialSecurityNumber
    + phoneNumber
    + salary
    + hourlyRate
  - Phương thức:
    + getEmployeeInfo(): Truy xuất thông tin nhân viên.
    + setEmployeeInfo(): Cập nhật thông tin nhân viên.

EmployeeUI
  - Nhiệm vụ: Giao diện cho Payroll Administrator để nhập và xem thông tin nhân viên.
  - Thuộc tính:
    + selectedFunction
    + inputData
  - Phương thức:
    + displayEmployeeInfo(): Hiển thị thông tin nhân viên.
    + enterEmployeeData(): Yêu cầu người dùng nhập thông tin nhân viên.
    + confirmDeletion(): Xác nhận thao tác xóa.
b) Quan hệ giữa các lớp
  - PayrollAdministrator sử dụng EmployeeUI để chọn chức năng (thêm, cập nhật, hoặc xóa).
  - EmployeeUI tương tác với EmployeeManager để thực hiện chức năng đã chọn và yêu cầu thêm thông tin   - từ lớp Employee khi cần.
  - EmployeeManager trực tiếp quản lý dữ liệu trong Employee, thực hiện các thao tác thêm, cập nhật hoặc xóa.

c) Biểu đồ lớp phân tích
![](https://www.planttext.com/api/plantuml/png/X5D1JiCm4Bpx5Nk4GpyGeQf81QaI84JX0TjusreuTl2kGH7YPHnu4b_0QPCsk2taaCFCP7TsT_Bz-JLXmI2niegVZOFWcLHfaHdkiGdUsajT6MTO0eeFyAuWFIF08JgR5c2ST9J3YWgOIp1kjO40c2oLSXrTASQxi_C2NhtHwaDrhQwgslg6w1OThcZVXJhy9dKge7rVzD9nLngrxg5TtIqJQur29qYT71qX3nmTMFbdrhtmiQbpAdaDn9oXx4k3Tavb34QQkrWjA6IIUkqT7MKOBOQc0EtZmb87hdqCjdb8q_yY05Oa_M0pj_JPJlW4Ux2KfzbkBTlBakvlczapheuoHS4i4DfmRR7vmmmveT3pROMCBxrRcb1DspjccJeQtD5eFFI_EI85B8NXpSXQ3RYXj4za0O5U8d6IusPGLhba-5dILnkO8OKGbPgGq-rFzWC00F__0m00)

# Phân tích ca sử dụng Run Payroll
1. Mô tả ngắn gọn

Ca sử dụng "Run Payroll" mô tả quá trình hệ thống tự động xử lý bảng lương cho nhân viên vào mỗi thứ Sáu và ngày làm việc cuối cùng của tháng. Hệ thống sẽ tính toán tiền lương dựa trên các thông tin liên quan như thời gian làm việc, đơn hàng, thông tin nhân viên và các khoản khấu trừ hợp pháp. Hệ thống sẽ in phiếu lương nếu phương thức thanh toán là thư hoặc nhận trực tiếp, hoặc tạo giao dịch ngân hàng nếu là chuyển khoản trực tiếp.

2. Các lớp phân tích
  - Boundary: PayrollUI: Đại diện cho giao diện hệ thống để hiển thị kết quả và trạng thái quá trình tính lương.
  - Entity:
    + Employee: Chứa thông tin về nhân viên, bao gồm mức lương, giờ làm, các khoản khấu trừ, và phương thức thanh toán.
    + Timecard: Lưu trữ thời gian làm việc của từng nhân viên, được sử dụng để tính lương.
    + Payroll: Thực hiện tính toán lương cho nhân viên dựa trên thông tin từ Employee và  Timecard.
    + BankTransaction: Đại diện cho giao dịch ngân hàng để xử lý các khoản lương qua phương thức chuyển khoản.

Controller: PayrollController: Điều khiển toàn bộ quá trình chạy bảng lương, từ việc lấy danh sách nhân viên, tính toán lương, đến việc in phiếu lương hoặc tạo giao dịch ngân hàng.

3. Biểu đồ tuần tự
![](https://www.planttext.com/api/plantuml/png/T5D1ReCm4Bpx5IjEYTHyW4CLGLALGwD89UhPDKknC3QobqFUraEVr2zqJKAIbfG3icTdTeR5_lxyMWUIdeREYD1g2zu555AHyx2NH--CEHGW0nmAePmb1YOyFsqD-bY_xWHQqdI4RTSRTqICLLvFSAaxLD9N4Ixp2JttZ20l9pIJjYszj843QMTZDIk5u4Ihnnl75FnWpnqMIt4JZ6bidS87qjRe3_rkS8eLcCbhMFrfPNGWS3NWcGyu2OHnheUQ9uDIDHTS03-_FSjyj7nsWm-BYLTKov5QvZFF9XBVd6-nkjEDlom59OqQZ2JS8J4GknQsTW-tsbD_hiuCx2WQoz9Gf7GyOkYG6bU13f1ij4T5iC7U1Kt9I9r7oSeKUkyKXd3pNwvXJZxBYpehPr7egdibIKCOoMW2telr8hL9W4UUxBLgLqF_Nx934PDf6_rLWwgz7mhjlGcFPwIJldroVeC6OxYYtY5MMF4nYQ8rl-8b-G400F__0m00)
4. Nhiệm vụ của từng lớp

  - PayrollUI: Khởi tạo quá trình xử lý bảng lương và hiển thị trạng thái hoặc kết quả cho người dùng.
  - PayrollController: Điều phối toàn bộ quy trình chạy bảng lương, lấy danh sách nhân viên, tính toán và thực hiện thanh toán dựa trên phương thức đã chọn.
  - Employee:Đại diện cho từng nhân viên và lưu trữ các thông tin chi tiết như mức lương, phương thức thanh toán và trạng thái xóa.
  - Timecard: Quản lý giờ làm việc của từng nhân viên để cung cấp dữ liệu tính lương.
  - Payroll: Thực hiện các phép tính cho lương ròng và áp dụng các khoản khấu trừ hợp pháp.
  - BankTransaction: Xử lý giao dịch ngân hàng cho các khoản thanh toán qua chuyển khoản.

5.Biểu đồ lớp

a) Các lớp phân tích và nhiệm vụ của từng lớp

PayrollUI
  - Nhiệm vụ: Giao diện người dùng để khởi tạo quá trình chạy bảng lương và hiển thị trạng thái hoặc kết quả.
  - Phương thức:
    + runPayroll(): Gửi yêu cầu chạy bảng lương tới PayrollController.
    + printPaycheck(empInfo: Employee, netPay: Float): In phiếu lương cho nhân viên.
    + displayPayrollStatus(status: String): Hiển thị trạng thái quá trình chạy bảng lương.

PayrollController
  - Nhiệm vụ: Điều phối toàn bộ quá trình chạy bảng lương, bao gồm lấy danh sách nhân viên, tính toán lương, và xử lý thanh toán.
  - Phương thức:
    + runPayroll(): Quản lý toàn bộ quá trình chạy bảng lương.
    + getEligibleEmployees(): List<Employee>: Lấy danh sách nhân viên đủ điều kiện nhận lương.
    + processEmployeePay(employee: Employee): Tính toán và xử lý thanh toán cho từng nhân viên.
    + markForDeletionIfNeeded(employee: Employee): Đánh dấu xóa nhân viên nếu cần.

Employee
  - Nhiệm vụ: Lưu trữ thông tin chi tiết của từng nhân viên và cung cấp các phương thức liên quan đến nhân viên.
  - Thuộc tính:
    + employeeId: String
    + salary: Float
    + paymentMethod: String
    + markedForDeletion: Boolean
  - Phương thức:
    + isEligibleForPayroll(currentDate: Date): Boolean: Kiểm tra điều kiện nhận lương.
    + getPaymentDetails(): Payment: Lấy thông tin thanh toán của nhân viên.

Timecard
  - Nhiệm vụ: Quản lý và cung cấp dữ liệu về giờ làm việc của nhân viên.
  - Thuộc tính:
    + employeeId: String
    + hoursWorked: Float
    + date: Date
  - Phương thức:
    + getHours(employeeId: String): Float: Lấy số giờ làm việc của nhân viên.

Payroll
  - Nhiệm vụ: Thực hiện các phép tính chi tiết cho quá trình chạy bảng lương.
  - Phương thức:
    + calculateNetPay(empInfo: Employee, hoursWorked: Float): Float: Tính lương ròng.
    + applyDeductions(empInfo: Employee): Float: Áp dụng các khoản khấu trừ hợp pháp.

BankTransaction 
  - Nhiệm vụ: Xử lý giao dịch ngân hàng cho các khoản thanh toán qua chuyển khoản.
  - Thuộc tính:
    + transactionId: String
    + amount: Float
  - Phương thức:
    + processTransaction(empInfo: Employee, netPay: Float): Boolean: Thực hiện giao dịch ngân hàng.

b) Quan hệ giữa các lớp
  - PayrollUI giao tiếp với PayrollController để khởi tạo quá trình chạy bảng lương và nhận trạng thái từ quá trình.
  - PayrollController tương tác với Employee để lấy danh sách nhân viên đủ điều kiện nhận lương.
  - PayrollController sử dụng Timecard để lấy dữ liệu giờ làm việc của từng nhân viên.
  - PayrollController gọi Payroll để tính toán lương ròng cho từng nhân viên.
  - PayrollController tương tác với BankTransaction nếu phương thức thanh toán của nhân viên là chuyển khoản trực tiếp.
  - PayrollController tương tác lại với Employee để đánh dấu xóa nhân viên nếu cần thiết sau khi xử lý lương.

c) Biểu đồ lớp phân tích
![](https://www.planttext.com/api/plantuml/png/X9JFYjim4CRlUWeTRMXUG9HbsMQN1jgbi5jwdbgpYOWi6OsqO4gVh8S-Kb-XactPZXsJ76BpUURJR_xO__xylISFpeTQCpehmvqbP9K68luDMcUr_dxWlnXFFnVCe1LbhpHE6H-rweJLkS2wEPWtA_XZtMZR8dxW1jDZmP-q1JyaIKMDXdQmUl7W0nNKNGH_yT7oMBBVx9BYapK-NT5jqnpHFsfrL3yrPW8gIi6_AF8VitANoMs5H5cDJWc_kv_u1zyQtFd9kZrgzCgQmzipeaHvDM7apjA0kyl11vcBx7K23Ivtg9SQQ6iq_Ylwarr49nIKCnZ17wpL2AP7LPGx46DoUwhWNFJRWu-ewRzSP1sxAQKpz-X1wQvhWp9LzAfghC39MnMTR73qmoRGYxBaUFvuwkSKMgoDofouN8Cy_0fq5NIqUkxGhwtU6gESut1e6jtkKOOgzP7M5ck81p3dLmU6eCl9ZV2JjEm5r3OOVt7ki7apdzilpZIlo3AzbxlTtPNtGt1bb5UnESJMJrFEk9k2Euoq-BuPEWvTy42RKNaw8bUt6RbiuHoMZLnRXKNtToMHUDmbO2FRpV3PBcIkpQJOaU0C3HDWI-1RQRDbw3zjx1wDJD_N_m000F__0m00)

# Phân tích biểu đồ Select Payment Method
1. Mô tả ngắn gọn

Ca sử dụng này cho phép Nhân viên chọn một phương thức thanh toán. Phương thức thanh toán sẽ quyết định cách Nhân viên nhận lương. Nhân viên có thể chọn một trong ba phương thức: nhận séc trực tiếp, nhận séc qua đường bưu điện, hoặc nhận lương qua chuyển khoản trực tiếp vào tài khoản ngân hàng đã đăng ký.

2. Các lớp phân tích
  - Boundary Class: PaymentUI
  - Controller Class: PaymentController
  - Entity Class: Employee, EmployeePayment
3. Biểu đồ tuần tự
![](https://www.planttext.com/api/plantuml/png/b5JBQjmm5DthAowppmy4N492eQLfo2A5TkdnY94OMpAs7EfbwQAKKEZGHRVZXb8QMff2L_PY5XhcF_G5_OLUoKxzcCaaySB6L-UUSy-nvB_LyY1LVgAoA2JfZ0j8P4g97oYPmECe3cLEAVWfK4B6CXCJFydXrCyZAjIBftOXuoIGGYKolAaVrQyXJUnwe9AGO9Mhl4yOnSDoq-zMOpydXCBU8nI0VJWqvIy5gxaflsKGC5Dz412pzVMw45DG-Fuzm8Sl62Yf2q6m2LkjDZQ_qbVOTDzMueSAJWU0aM2c_2b09QRwZNXkocKy8e2N4q4nEpAA7I4k1WTN4DUEdbF5v0IyssXecD9DoV7wEaFBt5JlH5_AHT9nvLXZ6qzruJkFxns-Je4Y-6GJ0Lr-1s_ZNdtSXUk5UvPakQdUY3ku7vHIppcSwmM4TQNZRtjc0RFJl1KmOzAKb_VBJJ7zntBWxXTJ_KK0qmintPwWqbSzb9ikDTKSLnRyHdOGvzbT0iCiTqpqe20tucZ3l4M2YWaX0urZYzzrP1okjV5I5m4qEtqrrvSsxVz3ajx7Q98PwqBQYHP86TWAQOD_mfq3Ati1hrjgGZmFZZDJVN93uGG8APVxyAnnfdz4hlGrxvbbrkmvjz_HyznXF-cKPWtIqkAzBFZc3kfD59hgCuVH5j6EqgZEzG3lzaVx3m00__y30000)
4. Nhiệm vụ của từng lớp phân tích
PaymentUI
  - Hiển thị các tùy chọn phương thức thanh toán cho nhân viên (nhận trực tiếp, bưu điện, chuyển khoản).
  - Nhận thông tin đầu vào từ nhân viên, như địa chỉ bưu điện (khi chọn phương thức bưu điện) hoặc thông tin ngân hàng (khi chọn phương thức chuyển khoản).
  - Hiển thị thông báo xác nhận hoặc lỗi cho nhân viên sau khi xử lý.
PaymentController
  - Nhận yêu cầu chọn phương thức thanh toán từ PaymentUI.
  - Kiểm tra và yêu cầu thông tin bổ sung nếu cần, dựa trên phương thức thanh toán được chọn (ví dụ, yêu cầu địa chỉ bưu điện hoặc thông tin ngân hàng).
  - Tương tác với lớp EmployeePayment để lưu thông tin phương thức thanh toán đã chọn.Truyền kết quả cập nhật thành công hoặc thông báo lỗi về PaymentUI.
Employee
  - Lưu trữ thông tin cơ bản của nhân viên, cần thiết để xác định danh tính khi chọn phương thức thanh toán.
  - Cung cấp các phương thức cần thiết để lấy thông tin nhân viên và kiểm tra tính hợp lệ của nhân viên.
EmployeePayment
  - Lưu trữ thông tin về phương thức thanh toán mà nhân viên đã chọn.
  - Lưu các thông tin bổ sung, như địa chỉ (với phương thức bưu điện) hoặc tên ngân hàng và số tài khoản (với phương thức chuyển khoản).
  - Cung cấp các phương thức để cập nhật và xác nhận thông tin thanh toán đã chọn.
5. Phân tích các lớp
a) Thuộc tính của từng lớp
PaymentUI (Boundary Class):
  - selectedMethod: Chuỗi biểu thị phương thức thanh toán đã chọn ("pick up", "mail", hoặc "direct deposit").
  - address: Chuỗi chứa địa chỉ, nếu phương thức thanh toán là "mail".
  - bankName: Chuỗi tên ngân hàng, nếu phương thức thanh toán là "direct deposit".
  - accountNumber: Chuỗi chứa số tài khoản, nếu phương thức thanh toán là "direct deposit".
PaymentController (Control Class):
  - employee: Đối tượng Employee đại diện cho nhân viên thực hiện lựa chọn.
  - payment: Đối tượng EmployeePayment đại diện cho thông tin thanh toán của nhân viên.
Employee (Entity Class):
  - employeeId: ID duy nhất của nhân viên.
  - name: Tên nhân viên.
  - position: Chức vụ của nhân viên.
EmployeePayment (Entity Class):
  - paymentMethod: Chuỗi phương thức thanh toán ("pick up", "mail", hoặc "direct deposit").
  - mailingAddress: Chuỗi địa chỉ nhận qua thư, nếu phương thức là "mail".
  - bankName: Tên ngân hàng, nếu phương thức là "direct deposit".
  - accountNumber: Số tài khoản ngân hàng, nếu phương thức là "direct deposit".
  - status: Trạng thái thanh toán (có thể là "active", "pending", v.v.).
b) Quan hệ giữa các lớp
  - PaymentUI ↔ PaymentController: PaymentUI tương tác với PaymentController để gửi phương thức thanh toán được chọn và nhận lại kết quả xác nhận hoặc lỗi.
  - PaymentController ↔ Employee: PaymentController có quan hệ với Employee để truy cập và xác minh thông tin nhân viên thực hiện lựa chọn phương thức thanh toán.
  - PaymentController ↔ EmployeePayment: PaymentController cũng liên kết với EmployeePayment để cập nhật thông tin thanh toán mới và xác nhận phương thức thanh toán.

c) Biểu đồ lớp
![](https://www.planttext.com/api/plantuml/png/h9DDJiCm48NtEONLLI8r5-W22G6BB2X84GTmusbhrN_oE48HucGiE19Nm4cSD7P0RCWgyOpdVVDcylNnYHUkYDK8MICe8dccdGJbNYhobX7_b0H1GEE0FO8xQxOZjRDSdKAGCcO1CJazK7NPKmbfSjFeLhbzAmzWenWXZACHj0loJyPnhJ0lGlG4hWuO8MEaoOka39xrwvrMHsubxKlawAXhPxuYUy_YHdsoire8i7F388tG7NZwX_0M0cQySZqFDIRjWJ3cav5fKplDI1XIymNLL7a5KwNEgxM_HYFlcquyyUPDPU_1KIvmOTjAEK3D06RPJo8eVJ7_TVi_I-1NBHfMm6yDesx2gjHH9wPkqoNS3jAByAZuon3gGJDsvFeJbEND3vko8viM0JVPEjHVc8VeyxouH_ixTxAzBpqqx6zy0m00__y30000)
d) Giải thích biểu đồ lớp
  - PaymentUI: Đây là lớp giao diện, chứa các thuộc tính về phương thức thanh toán đã chọn và thông tin bổ sung như địa chỉ hoặc thông tin ngân hàng. PaymentUI chịu trách nhiệm thu thập đầu vào từ nhân viên và hiển thị kết quả sau khi PaymentController xử lý.
  - PaymentController: Lớp điều khiển này quản lý quá trình xử lý chọn phương thức thanh toán. Nó chứa tham chiếu tới Employee (để truy xuất thông tin nhân viên) và EmployeePayment (để lưu thông tin thanh toán của nhân viên).
  - Employee: Lớp này đại diện cho nhân viên đang thực hiện lựa chọn phương thức thanh toán, chứa các thuộc tính cơ bản của nhân viên như ID, tên, và chức vụ.
  - EmployeePayment: Lớp lưu trữ thông tin thanh toán của nhân viên, bao gồm phương thức thanh toán và các thuộc tính liên quan. Lớp này kết nối với PaymentController để lưu trữ và quản lý thông tin thanh toán.
