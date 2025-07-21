---
created: 2024-02-26T07:32
updated: 2024-03-09T20:54
tags:
  - Web
  - DataBase
---
### Transactional và Analytical :
- Cần xác định bản chất của ứng dụng đang thiết kế trước khi áp dụng các quy tắc chuẩn hóa.
- Transactional : người dùng cuối quan tâm nhiều hơn đến CRUD. CSDL cho hệ thống này được gọi là `OLTP`.
- Analytical : người dùng cuối quan tâm nhiều hơn đến phân tích, báo cáo, dự báo ... Những loại CSDL này có số lần chèn và cập nhật data ít hơn. Mục đích chính là tìm nạp và phân tích data nhanh nhất có thể. CSDL cho hệ thống này được gọi là `OLAP`.

### Normalization && De-normalization :
- Normalization (chuẩn hóa): thông thường sẽ thiết kế bảng cho quan hệ 1-n, n-m,... 
- De-normalization : làm phẳng cấu trúc thành 1 bảng với nhiều cột giúp cho data người dùng hoàn toàn nằm trên 1 bảng làm cho việc tìm, phân tích sẽ nhanh hơn.
	![[Pasted image 20240226075400.png]]

>[!note]- Nên hay không việc chia nhỏ cấu trúc dữ liệu :
>- Khi việc truy vấn áp dụng nhiều hàm phân tích chuỗi như substring, char-Index thì nên chia nhỏ cấu trúc dữ liệu để câu truy vấn rõ ràng, tối ưu hơn (chia nhở về số lượng cột).
>- Không nên lạm dụng quy tắc khi không thật sự cần thiết, gây khó khăn trong lúc tạo, cập nhật data.
>- Thông thường chúng ra hay thiết kế database theo hướng đối tượng, mỗi đối tượng sẽ là bảng. Nhưng nếu đối tượng là giống nhau thì chúng ra có thể gộp chung lại 1 bảng sau đó thêm 1 trường để phân biệt hai đối tượng.
