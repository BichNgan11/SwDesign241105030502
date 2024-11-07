**Phân tích ca sử dụng Create Employee Report**

**- Biểu đồ sequence**

![Diagram](https://www.planttext.com/api/plantuml/png/X991RiGW34NtdCBBpg8NoA8QgUskg-O4BdWg90AfSKRYR5tqIBr2eP1HqioaB930pv__BRu_luvHa6KQd48jWU5v65r8HEejJDuW9-XJ51eKUR6Iu9N6mFB8LeWjAXsyS73jMgcv7UuVMcC7cWc5Ad5tKFMw03FS0TF7H57MufbTogsB7SIHj3sbtPxPmiZXR0tzOTV7fRDQwU2TF74slq7h-UOJDs8Q6qU7pNBJF2Xq0X7FhLL1NjSoj1dr5p8_KjYTUHRs9MWK6toZTwPpXTvEf1XjnUqCycyuMHxwof0tlzboQeri5l6sietvJ_dfWXNnOzxAp_q1003__mC0)

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
