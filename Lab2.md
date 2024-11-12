**I.Phân tích ca sử dụng Create Employee Report**

**1. Các Lớp Phân Tích**

-Employee:

Thuộc tính: name, id

Phương thức: createReport(), specifyReportCriteria(), saveReport()

-ReportCriteria:

Thuộc tính: reportType, beginDate, endDate, chargeNumber

-Report:

Thuộc tính: reportID, reportType, data

Phương thức: generate(), save(), discard()

-System:

Thuộc tính: currentUser

Phương thức: requestReportCriteria(), provideReport(), displayErrorMessage(), promptForMissingInfo()

**2. Biểu đồ sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/X991RiGW34NtdCBBpg8NoA8QgUskg-O4BdWg90AfSKRYR5tqIBr2eP1HqioaB930pv__BRu_luvHa6KQd48jWU5v65r8HEejJDuW9-XJ51eKUR6Iu9N6mFB8LeWjAXsyS73jMgcv7UuVMcC7cWc5Ad5tKFMw03FS0TF7H57MufbTogsB7SIHj3sbtPxPmiZXR0tzOTV7fRDQwU2TF74slq7h-UOJDs8Q6qU7pNBJF2Xq0X7FhLL1NjSoj1dr5p8_KjYTUHRs9MWK6toZTwPpXTvEf1XjnUqCycyuMHxwof0tlzboQeri5l6sietvJ_dfWXNnOzxAp_q1003__mC0)

**3.Nhiệm Vụ Của Các Lớp Phân Tích**

-Employee:

Tương tác với hệ thống để tạo và lưu báo cáo.

-ReportCriteria:

Lưu trữ thông tin về loại báo cáo, thời gian bắt đầu và kết thúc, và số dự án nếu có.

-Report:

Chứa logic để tạo báo cáo dựa trên tiêu chí và lưu hoặc hủy báo cáo.

-System:

Quản lý yêu cầu từ người dùng, hiển thị báo cáo và xử lý các yêu cầu lưu hoặc hủy báo cáo.

**4.Thuộc Tính Của Các Lớp:**

-Employee:

name: Tên của nhân viên (kiểu dữ liệu String)

id: ID của nhân viên (kiểu dữ liệu String)

-ReportCriteria:

reportType: Loại báo cáo (kiểu dữ liệu String)

beginDate: Ngày bắt đầu của báo cáo (kiểu dữ liệu Date)

endDate: Ngày kết thúc của báo cáo (kiểu dữ liệu Date)

chargeNumber: Số dự án nếu có (kiểu dữ liệu String)

-Report:

reportID: ID của báo cáo (kiểu dữ liệu String)

reportType: Loại báo cáo (kiểu dữ liệu String)

data: Dữ liệu của báo cáo (kiểu dữ liệu String)

-System:

currentUser: Người dùng hiện tại (kiểu dữ liệu String)

**5.Biểu đồ lớp phân tích**

![Diagram](https://www.planttext.com/api/plantuml/png/X5DBRi903Dtd55PMRILGsNQ5L41YqIvAUm2JCM6apAVs12cgUh8kUgHUeGP26mA2MOmcx_d5pnxFpzVtM19ogbsL5HMAmDJ5AZH4y961hW4i4bjVWaT7nuWrks-0JR062YPCz48nSBgvxJ8IgR2hPayziat45diXkFcNVcQjbMD5tn3lsDSc7cnDD3yigRH-U-g2v4q7QlN56hcavzejYVivp-UQJwuuQ7632RlLbUI9DVzfpSU8iL8WcsuB5eqaSdqxHSrCFhs9Ek_ecTvhadIfqP73nfgprwJPOuNDb3dm4ubWIITQ5zDCMIkYDkP-5VPU_sOc7-Km641-FnpUvVtxUsWdmP9aRLrNuXrwTN4nMgCExHL0Rs2jMwMQbZveHcT-lnzP0qiKtOFFnZeesvVm2m00__y30000)


**6.Quan Hệ Giữa Các Lớp:**

-Employee xác định ReportCriteria (Employee "1" -- "0..*" ReportCriteria: specifies)

-System quản lý ReportCriteria (System "1" -- "0..*" ReportCriteria: manages)

-System tạo và xử lý Report (System "1" -- "0..*" Report: generates and handles)

-Report được tạo dựa trên ReportCriteria (Report "1" -- "1" ReportCriteria: created based on)


**II.Phân tích ca sử dụng Login**

**1. Các Lớp Phân Tích**

-User:

Thuộc tính: username, password

Phương thức: login(), enterCredentials()

-AuthenticationService:

Thuộc tính: authToken

Phương thức: validateCredentials(username, password), generateAuthToken()

-System:

Phương thức: displayLoginScreen(), promptForRetry(), displayErrorMessage(), grantAccess()

**2.Biểu đồ sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/d951IWGn44NtEKKj5VG2lP0PH7Tk73r0cHHjC5tLLbL6-cmkF99NC644cs54C8j0gFV_hqy-tpysvgXUfn8mkYWy6cbuaie9TO7TOavJYCAkKc1R_PdOSqJFmZlIVOuKGjV0vTKtFK2HCVFPUJYy-wGJ0oYzLZA_LahT1Oirw5ZS9gHhf3Q0SQ8BcD7iJJIjdK-kDC0UIqxez9SH5Z-m47_80EsSD5ulEXAJjeWEFiWBzSPTUDnwL6JVnaZMwr8nWip_p4pPveBBZQheNJF4aNv9dLMcsMz5xybrwS6SmgPTxQk_0000__y30000)

**3.Nhiệm Vụ Của Các Lớp Phân Tích**

-User:

Tương tác với hệ thống để thực hiện đăng nhập.

-AuthenticationService:

Xác thực thông tin người dùng và quản lý mã thông báo xác thực.

-System:

Quản lý giao diện đăng nhập và xử lý các yêu cầu đăng nhập từ người dùng.

**4.Thuộc Tính Của Các Lớp:**

-User:

username: Tên đăng nhập của người dùng (kiểu dữ liệu String)

password: Mật khẩu của người dùng (kiểu dữ liệu String)

-AuthenticationService:

authToken: Mã thông báo xác thực (kiểu dữ liệu String)

-System:

currentUser: Người dùng hiện tại (kiểu dữ liệu String)

**5.Biểu đồ lớp phân tích**

![Diagram](https://www.planttext.com/api/plantuml/png/R58nJiGm4EppYjLL8962zggB45HSGxW7BFOgM3XsjBl9AKAyZ88dyGNiN4vA8jpOcXtlp8xz-_rp44NMllM5yIW29o66pmBIAg5MTg61Fc41MrgZNQAV8zi91HYYi-1ZuyBDxHAYeCGFJ3OT77f9rQzY5gjwVS-mGNKnrCI3CxHLnqHwZHyKvgvlCNh200DwPr5fsNjZ-6xhzUfiXXiAnAb5TPLOcgj7KMgtRapFdDHoJCifhPFEu_YSvwyD4srIw3YsdJv5VY7bSLsRxpuoHpwI23Qq9ZICGIjZKkrYS7gatVqEodBQBbRtu7BMQ5IAsVo2ys_M-noL50SADd-1Fm000F__0m00)

**6.Quan Hệ Giữa Các Lớp:**

-User và System: Người dùng tương tác với hệ thống để thực hiện đăng nhập (User "1" -- "1" System: interacts).

-System và AuthenticationService: Hệ thống sử dụng dịch vụ xác thực để xác nhận thông tin đăng nhập của người dùng (System "1" -- "1" AuthenticationService: uses).

**III.Phân tích ca sử dụng Create Administrative Report**

**1. Các Lớp Phân Tích**
   
-PayrollAdministrator:

Thuộc tính: name, id

Phương thức: createReport(), specifyReportCriteria(), saveReport()

-ReportCriteria:

Thuộc tính: reportType, beginDate, endDate, employeeNames

-Report:

Thuộc tính: reportID, reportType, data

Phương thức: generate(), save(), discard()

-System:

Thuộc tính: currentUser

Phương thức: requestReportCriteria(), provideReport(), displayErrorMessage(), promptForMissingInfo()

**2. Biểu Đồ Sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/Z9D1JiCm44NtFeMNTC45ia15i6I1o0cczXIDvDXXFAdaix7WI5m16vkg8QcQB2nv_DyVpq_o_VcrZm8iq-0K60ciNo5nSExH3kGf2aCkgaEOl0LEkazHS53eXIJfDnm3onEJ81Ce4xnajfMLMhFIzm_DfDE64GIh-cwdQha8ri1ECtvC66NUD7FNsio5dOuZ6ZgcpVpVDKSE9xBuZvjlBszVJphzZXwp6IwaTN-rnOOeBCNHGHkb-UyKED4HJir6wVpScgrbsf-ftBnm6zz5uLw20Q7W6xanpHLocM0PfXqkCyjVsv5uwAi6lVsTFoTZWEr514lRfhdb_7oM5VDzNifVyWC00F__0m00)

**3.Nhiệm Vụ Của Các Lớp Phân Tích**

-PayrollAdministrator:

Tương tác với hệ thống để tạo và lưu báo cáo.

-ReportCriteria:

Lưu trữ thông tin về loại báo cáo, thời gian bắt đầu và kết thúc, và tên nhân viên.

-Report:

Chứa logic để tạo báo cáo dựa trên tiêu chí và lưu hoặc hủy báo cáo.

-System:

Quản lý yêu cầu từ người dùng, hiển thị báo cáo và xử lý các yêu cầu lưu hoặc hủy báo cáo.

**4.Thuộc Tính Của Các Lớp**

-PayrollAdministrator:

name: Tên của quản trị viên (kiểu dữ liệu String)

id: ID của quản trị viên (kiểu dữ liệu String)

-ReportCriteria:

reportType: Loại báo cáo (kiểu dữ liệu String)

beginDate: Ngày bắt đầu của báo cáo (kiểu dữ liệu Date)

endDate: Ngày kết thúc của báo cáo (kiểu dữ liệu Date)

employeeNames: Danh sách tên nhân viên (kiểu dữ liệu List<String>)

-Report:

reportID: ID của báo cáo (kiểu dữ liệu String)

reportType: Loại báo cáo (kiểu dữ liệu String)

data: Dữ liệu của báo cáo (kiểu dữ liệu String)

-System:

currentUser: Người dùng hiện tại (kiểu dữ liệu String)

**5.Biểu đồ lớp phân tích**

![Diagram](https://www.planttext.com/api/plantuml/png/X5F1IiD04BtdAuQSL6YnLn6fj0e55R7w0TFiD2viTkFCjX34B_FW9_aBJfiKqpIqUrWsxytRUJCx-Vt-6Kj4Zgl29Pb34NZ6YeDpjwQmtafaZ87XCm5T0vX7jZu7ZmNj8zPilm7MmHh8c33I2vM1uzbvcv6IChkiQch2DX9Rx8JW-b_wbJIszXLTGxnbNwjoPskg-M51kVMRKniaRrhGWvPuNLzo0rIKBbH4JrgUT5FtfvnDJnXfS8CHsqNcv4bRIuUbxoF6IePisfsOLnAfwDh9LipauviGj_LC7okIUApV9OUrDRslfTbBXzKTS-174i6S3hH56U-LjI9gO-QNeVRQEqRfA8N10DBBuV0YxJxfLJCSLdlVr7WYla2lZev6QzIkrGBe3RphvbJJq3lDgEVwUeeDB51q3puPw-niVfG_0000__y30000)

**6.Quan Hệ Giữa Các Lớp**

-PayrollAdministrator xác định ReportCriteria (PayrollAdministrator "1" -- "0..*" ReportCriteria: specifies)

-System quản lý ReportCriteria (System "1" -- "0..*" ReportCriteria: manages)

-System tạo và xử lý Report (System "1" -- "0..*" Report: generates and handles)

-Report được tạo dựa trên ReportCriteria (Report "1" -- "1" ReportCriteria: created based on)

**IV.Phân tích ca sử dụng Maintain Purchase Order**

**1. Các Lớp Phân Tích**
   
-User:

Thuộc tính: userId, name

Phương thức: createPurchaseOrder(), updatePurchaseOrder(), deletePurchaseOrder(), retrievePurchaseOrder()

-PurchaseOrder:

Thuộc tính: orderId, customerName, orderDate, orderDetails, status

Phương thức: create(), update(), delete(), retrieve()

-System:

Thuộc tính: currentUser

Phương thức: displayOrderForm(), submitOrder(), displayOrder(), displayMessage()

**2. Biểu Đồ Sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/v9HFIiKm4CRtEKMMxKBSTo4FV0Yk5EGT82PJ3BH9dKmUz6mkF99NC7_QPrjfhRYqq0QQNsRcco_9nzlxmP50yct3X2IB_EG0sRFrHWdi-LFl25e6XZJr_D6ZV14E7b05Y4MKNzqCKCLReGs5TuOL9SlpaOmhAexmwi5HchxpHfAs9c3BSAu3gUl-GjmY28BhKwVYS8G624ec6k8opJ0UdgrSzwQs8K_4bhc2GC0bz1LhfgWQyXLsv3C-WwR1fJMrnZRzpoBKjmovMgLTruW-atcLIDfpAbKoQ1nmdrhmirwrehP3UzOAHkWIV5Cq0g66CypnLT69EaBO3utReRQOyXiUPVVLRgjogmg_MFOBnuQCVtDCfTtwtnmRsfYEQZxZc_Nc9ksiTcfHlWlsM3IMicALKUmGFl4s_0G00F__0m00)

**3. Nhiệm Vụ Của Các Lớp Phân Tích**
   
-User:

Tương tác với hệ thống để tạo, cập nhật và xóa đơn đặt hàng.

-PurchaseOrder:

Lưu trữ thông tin đơn đặt hàng và thực hiện các thao tác tạo, cập nhật và xóa đơn hàng.

-System:

Quản lý giao diện và điều hướng quy trình duy trì đơn đặt hàng. Xử lý yêu cầu từ người dùng và hiển thị kết quả tương ứng.

**4.Thuộc tính**

-User:

userId: ID của người dùng (kiểu dữ liệu String)

name: Tên của người dùng (kiểu dữ liệu String)

-PurchaseOrder:

orderId: ID của đơn đặt hàng (kiểu dữ liệu String)

customerName: Tên khách hàng (kiểu dữ liệu String)

orderDate: Ngày đặt hàng (kiểu dữ liệu Date)

orderDetails: Chi tiết đơn đặt hàng (kiểu dữ liệu List<String>)

status: Trạng thái của đơn đặt hàng (kiểu dữ liệu String)

-System:

currentUser: Người dùng hiện tại (kiểu dữ liệu String)

**5.Biểu đồ lớp phân tích**

![Diagram](https://www.planttext.com/api/plantuml/png/X5BBIiGm5DttAovTgT11jxCQ5mgp6106Fo1jhcCWB-vDHeBuPIxy97_1AAqs9SLkGiyvoJtd99_l7piEWa8qkXcqO8O7aSXfVIkDiee3YU08NXl8NmV7GCgUm0g39QBapp_0sIa90w48U6UyTWdnudBEHIzNEOaQrpZ2F0dFS_Qj6JrFsD8dZlXU_kTVI4d8N8B-sTc5pZjMGJaxejB5NYEmq89IgSorXiZp17b6hOfQ1VNeyyZ7n07DCl0GYT26HqOg3bNijKXJJVUEJ3c1OszKcFYzVN8BL-K1LVAG-nEdqMJr5RKtBNGTjDURpLNxTsbRCCBcdToCeLPrdjoGfsJbBpXfyrATkGNtOb52dveTMldzphy0003__mC0)

**6.Quan Hệ Giữa Các Lớp**

-PayrollAdministrator và Employee: Người dùng quản lý thông tin nhân viên (PayrollAdministrator "1" -- "0..*" Employee : manages).

-System và Employee: Hệ thống xử lý các yêu cầu liên quan đến thông tin nhân viên (System "1" -- "0..*" Employee : processes).

-Employee và PayrollAdministrator: Thông tin nhân viên thuộc về nhân viên quản lý bảng lương (Employee "1" -- "1" PayrollAdministrator : owned by).

**VI.Phân tích ca sử dụng Run Payroll**

**1.Các Lớp Phân Tích**

-PayrollSystem:

Thuộc tính: currentDate

Phương thức: runPayroll(), retrieveEmployees(), calculatePay(), generatePaycheck(), createBankTransaction(), sendBankTransaction()

-Employee:

Thuộc tính: employeeId, name, payType, salary, timecards, benefits, deductions, paymentMethod

Phương thức: getPayDetails(), isEligibleForPay()

-BankSystem:

Phương thức: processBankTransaction()

**2.Biểu Đồ Sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/Z9DDJiCm48NtFeMNxO8BT84AQbaZu0AEFGIh_ed6OoIVZGL7uWgCcqGXbO56YXJxpVlUM9vyVNpk4ocax9rGcYBAHrKmEdTdl0qs4IhU55tCmIWii_fS4e4N4CXIaKS_k5W0vlMz2gUfGhHmykPs3Tf9p67QsMp5IciL0w65TvXpKyipYpjfqz7PtdOE7Y9otKPdH6xre0YsGZcICEb2ylC7gGTYzG2ahAkXpVABPhLoEZkEgibcj8xEcZoeuhaLsHMftq2Vpi8rs1u2u4Wz6zTeS0b-ier5q2GD335PkZf48t14lSuNL27nWDWOrabDp380EvaWc4i2BTyBPJ4rEXamQaZfNn27YVh-ThBL7F81OtYrw2VnAGU-r3txw-_m3G00__y30000)

**3. Nhiệm Vụ Của Các Lớp Phân Tích**
   
-PayrollSystem:

Điều phối quy trình chạy bảng lương, bao gồm việc truy xuất thông tin nhân viên, tính toán lương, và xử lý thanh toán.

-Employee:

Lưu trữ thông tin về nhân viên và cung cấp chi tiết về lương và các khoản khấu trừ.

-BankSystem:

Xử lý các giao dịch ngân hàng cho các thanh toán bằng chuyển khoản.

**4.Thuộc tính**

-PayrollSystem:

currentDate: Ngày hiện tại khi chạy bảng lương (kiểu dữ liệu Date)

-Employee:
   
employeeId: ID của nhân viên (kiểu dữ liệu String)

name: Tên của nhân viên (kiểu dữ liệu String)

payType: Loại hình thanh toán (ví dụ: theo giờ, lương cố định) (kiểu dữ liệu String)

salary: Lương của nhân viên (kiểu dữ liệu double)

timecards: Danh sách các bảng chấm công của nhân viên (kiểu dữ liệu List<Timecard>)

benefits: Danh sách các lợi ích của nhân viên (kiểu dữ liệu List<Benefit>)

deductions: Danh sách các khoản khấu trừ (kiểu dữ liệu List<Deduction>)

paymentMethod: Phương thức thanh toán (ví dụ: chuyển khoản, séc) (kiểu dữ liệu String)

-BankSystem:
   
Không có thuộc tính cụ thể nào được liệt kê

**5.Biểu đồ lớp phân tích**

![Diagram](https://www.planttext.com/api/plantuml/png/b5DBQiCm4Dtx58DNII6XtOPYGaWAXHOAoGKKQPg8o9BHZ5DCwScww95wXSg9xDWkzAEDnqypez5xJv_l7tDYuRdCJIAD888dKNbdpBeYnXnU4mXh0al12BBq7YtNyGa6E3gjm9Ss5et64N_GnBUhl32kGip08tkDHsmGQXELAxScT1P6bYRq3Or6JTOIMMX3eCxVSVVC7LhqvtovHtduhMWXx67ZXIKXMJiBqcEe7g1_EfdGgc7Ti3jVud7obaHcc-ujgUl0Yjq1HlnUzN4hSkmZXQWsLT60aJiIHlWgOYVYDpf7ARpAW6D4tUr5uEvPSmRRSz3RNA8gJuDduVOnf6zJvC46ZyXxfo8rG-Pso46Q-DUglNNEeB2WQMNqJeVfxvol9H_QgyDQpMtFZ567mZk9HF-Lec_lz2Q5oGJIw-dqAhq8D6iTIpyMT6QRWROSB2cPu4NpFfa7dzIlwWi00F__0m00)

**6.Quan Hệ Giữa Các Lớp**

-PayrollSystem và Employee: Hệ thống bảng lương truy xuất thông tin từ các đối tượng nhân viên (PayrollSystem "1" -- "0..*" Employee : retrieves).

-PayrollSystem và BankSystem: Hệ thống bảng lương tương tác với hệ thống ngân hàng để xử lý các giao dịch thanh toán (PayrollSystem "1" -- "0..*" BankSystem : interacts with).

**VII. Viết code java mô phỏng ca sử dụng Maintain Timecard**

      public class Emloyee {
          private String employeeId;
          private String name;

          public Emloyee(String employeeId, String name) {
              this.employeeId = employeeId;
              this.name = name;
         }

          public String getEmployeeId(){
              return employeeId;
         }

         public String getName(){
              return name;
         }
      }
      import java.util.Date;

      public class Timecard{
          private String employeeId;
          private Data date;
          private int hoursWorked;

          public Timecard(String employeeId, Data date, int hoursWorked) {
              this.employeeId = employeeId;
              this.date = date;
              this.hoursWorked;
       }
          public String getEmployeeId() {
              return employeeId;
       }
          public Date getDate(){
              return date;
       }
          public int getHoursWorked(){
              return hoursWorked;
       }
    }
       import java.util.ArrayList;
       import java.util.Date;
       import java.util.List;

       public class TimecardSystem {
       private List<Timecard> timecards;

       public TimecardSystem() {
           this.timecards = new ArrayList<>();
    }

       public void addTimecard(String employeeId, Date date, int hoursWorked) {
          Timecard timecard = new Timecard(employeeId, date, hoursWorked);
          timecards.add(timecard);
          System.out.println("Timecard added for employee: " + employeeId);
    }

        public void updateTimecard(String employeeId, Date date, int hoursWorked) {
          for (Timecard timecard : timecards) {
             if (timecard.getEmployeeId().equals(employeeId) && timecard.getDate().equals(date)) {
                timecards.remove(timecard);
                timecard = new Timecard(employeeId, date, hoursWorked);
                timecards.add(timecard);
                System.out.println("Timecard updated for employee: " + employeeId);
                return;
            }
        }
        System.out.println("Timecard not found for employee: " + employeeId);
    }

        public void deleteTimecard(String employeeId, Date date) {
          timecards.removeIf(timecard -> timecard.getEmployeeId().equals(employeeId) && timecard.getDate().equals(date));
          System.out.println("Timecard deleted for employee: " + employeeId);
    }

        public void retrieveTimecards(String employeeId) {
          System.out.println("Timecards for employee: " + employeeId);
            for (Timecard timecard : timecards) {
               if (timecard.getEmployeeId().equals(employeeId)) {
                  System.out.println("Date: " + timecard.getDate() + ", Hours Worked: " + timecard.getHoursWorked());
            }
         }
      }
    }
 
         import java.util.Calendar;
         
         public class Main {
         public static void main(String[] args) {
            TimecardSystem timecardSystem = new TimecardSystem();

            timecardSystem.addTimecard("E001", Calendar.getInstance().getTime(), 8);

            timecardSystem.updateTimecard("E001", Calendar.getInstance().getTime(), 9);

            timecardSystem.retrieveTimecards("E001");

            timecardSystem.deleteTimecard("E001", Calendar.getInstance().getTime());
            timecardSystem.retrieveTimecards("E001");
      }
    }
    
