**LAB 1**

**PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG**

**1. Phân tích kiến trúc**
![Diagram](https://www.planttext.com/api/plantuml/png/j5HBJiCm4Dtx5AEksaKt702L41P8HLGji9ywqs9mx6ZiW2BKax7WI5m1frK_SHFQ1Sp22y_pcpSlC_d-_1evZ-pBN8i2vIik2NeJhDXg3RFAUSfxy24Wn3xDvCXuzCeQ66D5l8NK8JKw1xsRlD2s8e9RuuaNAEaGj8u7bPD4pbppUbAoV4P7SCyPSPnaMX2JaRHFhCJcRAfCIgSC1IbZkrIoKsVeDG_Dm8puJRM8l4OjIusU-eDOYGqYtC7rAkRUDjX9FYldkV8nynDgbJKh7b4tJUeiC2LfEJkxGEnXYXxXIigrZISCd59XdVAMgoCL6uPOnMDHQu0qESl2_w6FRFp38crMpkjA9nTcYmoOJZlShwXeWuAyDjIObYYhUevVI7guGnE4hZzbca0_JIu6krSh4TfftVjXPj_DyB9ZtKJ75kvU7G-OQ1kw1lx0HJ4YazM_hXy0003__mC0)
**-Lý do lựa chọn:**

Tính tách biệt rõ ràng: Mỗi lớp có nhiệm vụ riêng, giúp dễ dàng bảo trì và phát triển.

Khả năng mở rộng: Dễ dàng thêm mới hoặc sửa đổi các thành phần mà không ảnh hưởng đến toàn hệ thống.

Tính tái sử dụng: Các thành phần có thể được tái sử dụng trong các module khác của hệ thống.

Bảo mật tốt hơn: Giúp bảo vệ dữ liệu và nghiệp vụ khi chỉ cho phép truy cập qua các lớp được xác định trước.

**-Ý nghĩa từng thành phần trong kiến trúc:**

**Presentation Layer (Lớp trình bày):**

Employee Interface: Giao diện người dùng cho phép nhập thông tin thời gian làm việc (Timecards), đơn hàng (Purchase Orders), và tùy chọn thanh toán (Preferences). Lớp này chịu trách nhiệm hiển thị thông tin và nhận đầu vào từ người dùng.

**Business Logic Layer (Lớp logic nghiệp vụ):**

Payment Service: Xử lý các tác vụ tính toán và xử lý thanh toán cho nhân viên.

Timecard Service: Quản lý việc nộp và xác nhận thông tin thời gian làm việc của nhân viên.

Purchase Order Service: Xử lý việc ghi nhận và xác nhận thông tin về các đơn hàng mà nhân viên bán hàng ghi nhận.

**Data Access Layer (Lớp truy cập dữ liệu):**

Payment Repository: Truy cập và cập nhật cơ sở dữ liệu liên quan đến thanh toán.

Timecard Repository: Truy cập và cập nhật cơ sở dữ liệu liên quan đến thời gian làm việc.

Purchase Order Repository: Truy cập và cập nhật cơ sở dữ liệu liên quan đến đơn hàng.

**-Database Layer (Lớp cơ sở dữ liệu):**

Employee Database: Lưu trữ thông tin về nhân viên.

Timecards Database: Lưu trữ thông tin về thời gian làm việc của nhân viên.

Purchase Orders DB: Lưu trữ thông tin về các đơn hàng mà nhân viên bán hàng ghi nhận.

Legacy Project Management DB (DB2): Cơ sở dữ liệu quản lý dự án hiện có, lưu trữ thông tin về dự án và số liệu tính phí, không thay đổi.

**2. Cơ chế phân tích**

-**Các cơ chế cần giải quyết trong bài toán**

Xác thực và ủy quyền (Authentication & Authorization):

Lý do: Đảm bảo chỉ có nhân viên hợp lệ mới được truy cập hệ thống và bảo mật thông tin cá nhân.

Quản lý giao dịch (Transaction Management):

Lý do: Đảm bảo tính toàn vẹn của dữ liệu khi thực hiện các giao dịch.

Xử lý lỗi (Error Handling):

Lý do: Xác định cơ chế xử lý lỗi và thông báo lỗi cho người dùng.

Caching:

Lý do: Sử dụng bộ nhớ đệm để cải thiện hiệu suất hệ thống.

Tích hợp hệ thống cũ (Legacy System Integration):

Lý do: Đảm bảo hệ thống mới hoạt động mượt mà với cơ sở dữ liệu quản lý dự án hiện có.

**3. Phân tích ca sử dụng Payment**

![Diagram]
(https://www.planttext.com/api/plantuml/png/T9112i9034NtSufSm0lCGWeYua8eYWSOfhzOc9cKJ1HwDXSUoIlOGgj5RLOX-Iy_oVF-AB8wqMiCndbbeMri0tU0cH9QhQbqNKJI3ISL3W5YwOG0hrE73j0BL-P7EADFa5lZOQaKziXvWHrb0pYjS4JBkUctwopjeEywxLFDVxYnCiVERUKK2vOVuTpLKdz6tKZyeiPPfa2gXh_ryG800F__0m00)

**-Các lớp phân tích và biểu đồ sequence**

**Các lớp phân tích:**

PaymentController

PaymentService

EmployeeRepository

PaymentRepository

**4. Phân tích ca sử dụng Maintain Timecard**

![Diagram]
(https://www.planttext.com/api/plantuml/png/R9112eD034NtSufSe1UOHH5AATtMqlrK8mHc9fA9WcTpqIFr2bNQiOBkmiz__9-ynrUHr8bsmHjNAGkSG-jvG3HvWCCHxXImSbAVEAgmzoWMokuPI9ULsNhMP8dIKuKM7ivJxHItuCyoKpdxXYqdcceD5YweYmxNsF0UcAKrMBf-9-tlM0TQcEet9641ldUcH1nDWR6UFsK-0000__y30000)

**-Các lớp phân tích và biểu đồ sequence**

**Các lớp phân tích:**

PaymentController

PaymentService

EmployeeRepository

PaymentRepository
