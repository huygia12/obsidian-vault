---
created: 2024-02-25T11:31
updated: 2023-04-18T00:26
tags:
  - Java
---
## Definition:
- Được tạo ra để xử lý những trường hợp tung ra `NullPointerException`
- Optional Object có thể chưa 1 non-null value hoặc không chưa một value nào cả
- Optional object có thể có hai trạng thái:
	- Present: Có một giá trị trong Optional Object và nó có thể được lấy ra thông qua get()
	- Absent: Đại diện cho sự vắng mặt của giá trị, không thể lấy được thông qua get()
## Khởi tạo 1 Optional Object:

- of(): Khởi tạo với 1 giá trị cho trước và trả về Optional Object chứa giá trị đó, không thì trả về `empty optional object`
- empty(): khởi tạo 1 `empty optional object`
- ofNullable(): trả về giá trị nếu nó là non-null, nếu null thì tung ra `NoSuchElementException`
- isPresent(): kiểm tra xem object có chưa giá trị non-null hay không.
- getOrElse(): trả về giá trị nếu nó non-null, nếu null thì trả về giá trị trong ngoặc
- ifPresent(): vẫn là kiểm tra xem object có phải non-null hay không nhưng nếu đúng thì thực hiện câu lệnh là biểu thức lambda trong ngoặc đơn.
- map() : để chuyển đổi từ kiểu dữ liệu của Optional gọi hàm này sang kiểu dữ liệu của Optional khác là kết quả của biểu thức lambda trong ngoặc đơn

## Lưu ý: 
- Optional Object có thể được triển khai ở bất cứ đâu để ngăn chặn `NULLPointerException` bị quăng ra màn hình nhưng nó sẽ là hiệu quả nhất khi để nó là giá trị trả về của một phương thức nào đó để người đọc hiểu rằng khi gọi hàm này, giá trị nhận lại có thể không tồn tại và họ phải xử lý nó.