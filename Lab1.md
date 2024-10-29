**LAB 1**

**PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG**

**1. Phân tích kiến trúc**

**-Biểu đồ package mô tả kiến trúc.**

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

**-Biểu đồ sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/T9112i9034NtSufSm0lCGWeYua8eYWSOfhzOc9cKJ1HwDXSUoIlOGgj5RLOX-Iy_oVF-AB8wqMiCndbbeMri0tU0cH9QhQbqNKJI3ISL3W5YwOG0hrE73j0BL-P7EADFa5lZOQaKziXvWHrb0pYjS4JBkUctwopjeEywxLFDVxYnCiVERUKK2vOVuTpLKdz6tKZyeiPPfa2gXh_ryG800F__0m00)

**-Các lớp phân tích:**

**PaymentController**

Nhiệm vụ: Điều khiển việc chọn phương thức thanh toán và giao tiếp với PaymentService để xử lý logic nghiệp vụ.

Thuộc tính: paymentService: PaymentService

Phương thức: selectPaymentMethod()

**PaymentService**

Nhiệm vụ: Xử lý nghiệp vụ liên quan đến việc chọn phương thức thanh toán, truy cập EmployeeRepository để lấy thông tin nhân viên và PaymentRepository để cập nhật phương thức thanh toán.

Thuộc tính:

employeeRepository: EmployeeRepository

paymentRepository: PaymentRepository

Phương thức: processPaymentMethod(employeeId: int, method: PaymentMethod)

**EmployeeRepository**

Nhiệm vụ: Cung cấp các phương thức để truy cập thông tin nhân viên từ cơ sở dữ liệu.

Phương thức: getEmployeeById(employeeId: int)

**PaymentRepository**

Nhiệm vụ: Cung cấp các phương thức để cập nhật phương thức thanh toán của nhân viên trong cơ sở dữ liệu.

Phương thức: updatePaymentMethod(employeeId: int, method: PaymentMethod)

**Employee**

Thuộc tính:

id: int

name: String

paymentMethod: PaymentMethod

**PaymentMethod (Enum)**

Giá trị:

PICK_UP

MAIL

DIRECT_DEPOSIT

**Biểu đồ lớp mô tả lớp phân tích**

![Diagram](https://www.planttext.com/api/plantuml/png/b5F1JiCm3BttAwoTG68_a0CQ30uxm84DSVPIgukMDbMSJgeGNyQ1J-8NI4lNfMt6HAJsuFVy_6mdtvzV2tPeNPNhf4IvnunWzeIgSFw3ZSf9eatXbGcMo3I3zmJyaHgPUtXf2cUDrcGxk3bpS1sy9djGaaJFxm8z5O2hRQxS4R-wRg6F95AhonqKehpKfYPweTAmSiRM0XudiOYpC64pYGN-3gXLYexkYdID1-gD7YklKW5-PZUzyaalqilKMz0EG4RkoBYlLvCYVmpdZ227bl_bS31czLi_Y1IO-xMkdLL5TjxL1P5HUm7IJ5p0W_y7mPsfBByPkoVFJqsrrI4gTsWpUgxoBTcHC-yjSc7djvEh9Q1YucGSzip8uWIWbCHd4YAB4UqwE8be1HKyJPhs4PvqXyn-kW5pGKNQlEJs_0000F__0m00)

**-Giải thích**

PaymentController: Điều khiển việc chọn phương thức thanh toán, sử dụng PaymentService để xử lý logic nghiệp vụ.

PaymentService: Xử lý nghiệp vụ liên quan đến việc chọn phương thức thanh toán, truy cập EmployeeRepository để lấy thông tin nhân viên và PaymentRepository để cập nhật phương thức thanh toán.

EmployeeRepository: Cung cấp các phương thức để truy cập thông tin nhân viên từ cơ sở dữ liệu.

PaymentRepository: Cung cấp các phương thức để cập nhật phương thức thanh toán của nhân viên trong cơ sở dữ liệu.

Employee: Lớp đại diện cho nhân viên, bao gồm các thuộc tính như id, name và paymentMethod.

PaymentMethod: Enum để định nghĩa các phương thức thanh toán (PICK_UP, MAIL, DIRECT_DEPOSIT).

**4. Phân tích ca sử dụng Maintain Timecard**

**-Biểu đồ sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/R9112eD034NtSufSe1UOHH5AATtMqlrK8mHc9fA9WcTpqIFr2bNQiOBkmiz__9-ynrUHr8bsmHjNAGkSG-jvG3HvWCCHxXImSbAVEAgmzoWMokuPI9ULsNhMP8dIKuKM7ivJxHItuCyoKpdxXYqdcceD5YweYmxNsF0UcAKrMBf-9-tlM0TQcEet9641ldUcH1nDWR6UFsK-0000__y30000)

**Các lớp phân tích:**

**TimecardController**

Nhiệm vụ: Điều khiển việc nộp thông tin thời gian làm việc và giao tiếp với TimecardService để xử lý logic nghiệp vụ.

Thuộc tính: timecardService: TimecardService

Phương thức: submitTimecard()

**TimecardService**

Nhiệm vụ: Xử lý nghiệp vụ liên quan đến việc nộp thông tin thời gian làm việc, truy cập EmployeeRepository để lấy thông tin nhân viên và TimecardRepository để lưu thông tin thời gian làm việc.

Thuộc tính:

employeeRepository: EmployeeRepository

timecardRepository: TimecardRepository

Phương thức: validateAndSaveTimecard(employeeId: int, timecard: Timecard)

**EmployeeRepository**

Nhiệm vụ: Cung cấp các phương thức để truy cập thông tin nhân viên từ cơ sở dữ liệu.

Phương thức: getEmployeeById(employeeId: int)

**TimecardRepository**

Nhiệm vụ: Cung cấp các phương thức để lưu thông tin thời gian làm việc vào cơ sở dữ liệu.

Phương thức: saveTimecard(timecard: Timecard)

**Employee**

Thuộc tính:

id: int

name: String

**Timecard**

Thuộc tính:

id: int

employeeId: int

date: Date

hoursWorked: double

chargeNumber: String

**-Các lớp phân tích và biểu đồ sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/h5DBReCm4DrpYb5MhTHSW4MLbcI1MbGKadLacH55nH_PfXAgUh8kUgHUeH0CCXXscTtCFDvxdXd-VdvtsX1bQbO5aj0FKY1iKj8mv0RE6Y4Y6ZVm5K0Rj29QW-r6WXibgWgLxNQn1TbtCrIV9SLmGDjy109eh90QsqxGl8lyxlxQ_mvyDVlzH0gPh4I3U4GfT6c4Qa8uU3NVcujFvoN7eLI2ejPJYuDed8TGSlC0x5eVcNhOmaDyPyvZ00eq0-AvYJsTzSciyDKo9mPlx7qo_h9dSIgSi7RZcL4bB_on9qjYhXRocasxZbuQHo-NSphcoLFyEYRx-7Y8JfVz8NtBufFbR5dzKzq-pYygX5gZ3cRL5hUmi108xKvY4U_l8xHRqC42bwFG0cbhaPHyv5q53emxv7dtqtRn3m00__y30000)

**Giải thích**

TimecardController: Điều khiển việc nộp thông tin thời gian làm việc, sử dụng TimecardService để xử lý logic nghiệp vụ.

TimecardService: Xử lý nghiệp vụ liên quan đến việc nộp thông tin thời gian làm việc, truy cập EmployeeRepository để lấy thông tin nhân viên và TimecardRepository để lưu thông tin thời gian làm việc.

EmployeeRepository: Cung cấp các phương thức để truy cập thông tin nhân viên từ cơ sở dữ liệu.

TimecardRepository: Cung cấp các phương thức để lưu thông tin thời gian làm việc vào cơ sở dữ liệu.

Employee: Lớp đại diện cho nhân viên, bao gồm các thuộc tính như id và name.

Timecard: Lớp đại diện cho thông tin thời gian làm việc, bao gồm các thuộc tính như id, employeeId, date, hoursWorked và chargeNumber.

**5. Hợp nhất kết quả phân tích**

**Hợp nhất kết quả phân tích của hai ca sử dụng: Select Payment và Maintain Timecard**

**-Biểu đồ sequence hợp nhất**

![Diagram](https://www.planttext.com/api/plantuml/png/X95D3e8m48NtFKMNkl02B0mBMBWm8V5dFxPZ92aj6OO5PtFXaRo2HQG8IDmrVM_UbpVpl3_YYe6uBem0nOvaMfJ6DOX2N5njDL0ZTvQHhg3ydtAMoHcPGLEWvOoSmgfo58HZNg02qeCY-aIvsGvHaJoWGSLzajmZtvmMmT2wfvH8di7a6XW_IZUqMekfSy8QGqBANzof_88bo92RojEMAgNjCwn09i0m9iosCpJg9Pz1ZMVCh1DMeBm7bYhz07QTUi6JOhIwlVyB003__mC0)

**-Biểu đồ này thể hiện hai ca sử dụng chính:**

**Select Payment:**

Nhân viên chọn phương thức thanh toán qua giao diện.

Giao diện gửi yêu cầu xác thực phương thức thanh toán đến PaymentProcessor.

PaymentProcessor xác thực phương thức thanh toán và gửi phản hồi về giao diện.

Giao diện cập nhật chi tiết phương thức thanh toán của nhân viên thông qua PaymentProcessor.

**Maintain Timecard:**

Nhân viên nhập dữ liệu thẻ thời gian qua giao diện.

Giao diện gửi yêu cầu xác thực dữ liệu thẻ thời gian đến TimecardProcessor.

TimecardProcessor xác thực dữ liệu thẻ thời gian và gửi phản hồi về giao diện.

Giao diện cập nhật dữ liệu thẻ thời gian của nhân viên thông qua TimecardProcessor.

**-Biểu đồ lớp hợp nhất**

**Mô Tả Các Thành Phần**

**Employee (Nhân viên):**

**Thuộc tính:**

EmployeeID: Mã số nhận diện của nhân viên.

Name: Tên của nhân viên.

Address: Địa chỉ của nhân viên.

PaymentMethod: Phương thức thanh toán mà nhân viên chọn.

**Phương thức:**

SelectPaymentMethod(): Nhân viên chọn phương thức thanh toán.

EnterTimecard(): Nhân viên nhập dữ liệu thẻ thời gian.

**PaymentMethod (Phương thức thanh toán):**

**Thuộc tính:**

MethodType: Loại phương thức thanh toán (ví dụ: Chuyển khoản trực tiếp, gửi qua bưu điện).

PaymentProcessor (Bộ xử lý thanh toán):

**Phương thức:**

ValidatePaymentMethod(): Xác thực phương thức thanh toán mà nhân viên chọn.

UpdatePaymentDetails(): Cập nhật thông tin chi tiết về phương thức thanh toán của nhân viên.

**Timecard (Thẻ thời gian):**

**Thuộc tính:**

Date: Ngày làm việc được ghi nhận.

HoursWorked: Số giờ làm việc được ghi nhận.

ChargeNumber: Số mã phí liên quan đến công việc.

TimecardProcessor (Bộ xử lý thẻ thời gian):

**Phương thức:**

ValidateTimecardEntry(): Xác thực các mục nhập thẻ thời gian.

UpdateTimecard(): Cập nhật thông tin thẻ thời gian của nhân viên.

**Mối Quan Hệ Giữa Các Thành Phần**

Employee có quan hệ với PaymentMethod: Nhân viên có thể chọn và cập nhật phương thức thanh toán của mình.

Employee có quan hệ với Timecard: Nhân viên có thể nhập dữ liệu thẻ thời gian của mình.

PaymentMethod liên kết với PaymentProcessor: Phương thức thanh toán được xác thực và cập nhật thông qua bộ xử lý thanh toán.

Timecard liên kết với TimecardProcessor: Thẻ thời gian được xác thực và cập nhật thông qua bộ xử lý thẻ thời gian.

![Diagram](https://www.planttext.com/api/plantuml/png/T5113e8m4Bpt5JtgWI-O627HWyG3whdIZH1RIhRbq1XVvi4d-GMnGAKIRZkpivtfl9-lN32jQI9heIm0lHDA8mztiOCfa-26DUS8MhlvmAo4okp158gt3AN7cZC30RzOkarI6S2ib90p_78FGZhVGDoRTo2pDKnq1rHvww_GIIazCL7EUGPfOZ2i57fiFSJfNUDMx8QjQb2V5Tw0Exmf65uXRUG5S7ezbsZOjpz76oGAQ_35Hz7ghz9WDLmH7tlC-XGaB7Jqw4_o0G00__y30000)
