---
created: 2024-03-23T13:59
updated: 2024-03-23T15:55
tags:
  - Diagram
---
## Concept :
- ***Actor*** : Là bất kỳ thứ gì tương tác với hệ thống mà có sự trao đổi dữ liệu với hệ thống (người dùng, thiết bị phần cứng, hệ thống phần mềm khác). Actor là 1 lớp người dùng chứ không phải 1 thể hiện cụ thể.
	- Actor không phải là 1 phần của hệ thống.
	- Actor trao đổi thông tin với hệ thống.
	- Tên Actor là danh từ.
- ***Use case*** : Là 1 chuỗi hành động mà hệ thống thực hiện nhằm thu được 1 kết quả dễ thấy bởi 1 Actor nào đó.
	- Tên của tác nhân nên là 1 động từ mô tả ngắn gọn mục đích ca sử dụng.
	

## Actors relationship :
- Tổng quát hóa (generalization) 
	- Actor con kế thừa tính chất và hành vi của Actor cha.
	![[Pasted image 20240323143701.png]]
- Giao tiếp (Association)
	![[Pasted image 20240323143642.png]]


## Actor and UC relationship :
- Giao tiếp (Association)
	- Một UC được bắt đầu với 1 tác nhân để gọi 1 chức năng nào đó trong hệ thống.
	![[Pasted image 20240323144116.png]]


## UCs relationship :
- Tổng quát hóa (generalization)
	- Sử dụng cơ chế kế thừa : mô tả hành vi chung trong UC cha, ngược lại với UC con.
	![[Pasted image 20240323144432.png]]

- Bao hàm (include) 
	- Tích hợp các UC như là phân đoạn trong hành vi tổng thể của nó.
	![[Pasted image 20240323144609.png]]

- Mở rộng (extend)
	- Mở rộng thêm chức năng tùy chọn của 1 UC.
	![[Pasted image 20240323144725.png]]


## Defection :
- Khó khăn khi dự án trở nên phức tạp, biểu đồ UC có thể trở nên rất lớn.
- Sự mơ hồ về chi tiết : không thể hiện chi tiết cách các chức năng thực hiện bên trong use case.
- Không thể hiện được luồng đi của dữ liệu.
## Note : 
- Actor không phải là 1 phần của hệ thống.
- Tránh tạo cá UC quá nhỏ, hành động quá đơn giản.
- Tránh tạo quá nhiều UC.
	- Nhóm các UC liên quan thành 1 UC tổng quát (mức 1).
	- Mô tả các UC tổng quát ở một biểu đồ khác (múc 2).
