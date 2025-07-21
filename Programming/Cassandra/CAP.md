---
created: 2024-02-25T11:29
updated: 2024-03-04T00:20
tags:
  - BackEnd
  - DataBase
---
## CAP theorem :
- Nguyên lý trong lĩnh vực distributed database: Trong 1 hệ thống phân tán(replication), **chỉ có thể đạt được hai trong ba tính chất** sau:
	- ***Consistency*** (tính nhất quán): mọi node trong hệ thống sẽ nhìn thấy cùng một bản sao của dữ liệu bất kỳ thời điểm nào. Nếu 1 nút thay đổi thì mọi nút khác cũng sẽ nhìn thấy thay đổi đó ngay lập tức.
	- ***Availability*** (Tính sẵn có): mọi yêu cầu đến hệ thống sẽ nhận được một phản hồi. Bất kể trạng thái của nút là gì trong hệ thống. Hệ thống phải luôn sẵn sàng để phản hồi yêu cầu, dù một số nút có thể gặp sự cố.
	- ***Partition tolerance*** (Tính chịu phân mảnh): hệ thống vẫn tiếp tục hoạt động một cách chính xác, dù một số nút trong hệ thống bị tách ra khỏi nhau (partitioned), có nghĩa là không có kết nối mạng giữa chúng.

  
- Dựa vào việc ưu tiên một trong ba tính chất, đưa ra quyết định phù hợp với yêu cầu và mục tiêu của ứng dụng cụ thể.
- VD: Hệ thống SQL (quan hệ) ưu tiên tính nhất quán, tính sẵn có. Hệ thống No-SQL ưu tiên tính sẵn có, tính chịu phân mảnh.
	![The CAP Theorem in DBMS - GeeksforGeeks](Exported%20image%2020240225112926-0.png)