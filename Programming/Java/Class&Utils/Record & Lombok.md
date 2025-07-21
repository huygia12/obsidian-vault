---
created: 1970-01-01T08:00
updated: 2024-03-28T15:20
tags:
  - Java
---
## Record :
#### Definition
- Là 1 từ khóa mới xuất hiện từ Java JDk 16. Mục đích để tạo một Immutable POJO.
	- Có 1 Constructor với tham số được cung cấp. Có thể thêm logic vào trong Constructor đó (tự truyền lại các tham số) nhưng không được thay đổi tham số truyền vào.
	- Record chỉ có getter, vẫn có thể viết thêm các phương thức khác vào record.
	- Chúng ta chỉ có thể truyền tham số vào record tại thờ điểm khởi tạo bằng constructor. Record đảm bảo rằng trong quá trình truyền lại không cho phép code sửa đổi nội dung thuộc tính bên trong. 
#### Note
- Record chỉ dùng khi đóng gói, truyền dữ liệu qua lại, data transfer object,... không thể dùng để mô hình Entity trong *JPA*.
- Thích hợp sử dụng trong môi trường lập trình *Concurreny* và *Multi-thread*.

---

## Lombok :
#### Definition
- Là 1 thư viện trong Java giúp giảm bớt việc viết boilerplate code khi tạo một class *POJO* (Plain Old Java Object) chỉ đơn giản để chứa dữ liệu.
#### Annotation 
- *@Data* : Chỉ áp dụng cho Class, sẽ sinh các get/set, toString, equals, hashCode.
- *@AllArgsContructor* :  Sinh ra Constructor chứa đầy đủ tham số tương ứng với thuộc tính của class.
- *@Builder* : tạo builder pattern cho đối tượng.
![](Pasted%20image%2020240712195846.png)