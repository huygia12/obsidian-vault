---
created: 2024-02-25T11:30
updated: 2023-11-20T15:24
---
## static:
- Các thành phần static sẽ được khởi tạo trước khi đối tượng được khởi tạo, các đối tượng cùng một class sẽ dùng chung vùng ô nhớ này.
- Có thể truy cập đến một thành phần static thông qua tên class mà không cần tham chiếu đến một đối tượng cụ thể.
## final: 
- Khai báo các thành phần hằng trong class, áp dụng được cho cả thuộc tính và phương thức, class.
	- final attribute: không thể thay đổi giá trị thuộc tính(constant)
	- final method: không thể ghi đè phương thức(override)
	- final class: không thể kế thừa từ class này

- Cú pháp: [Phạm_vi] final <kiểu> tên_hằng = giá_trị;

![Exported image](Exported%20image%2020240225113023-1.png)