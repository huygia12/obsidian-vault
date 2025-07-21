---
created: 2024-02-26T16:05
updated: 2024-02-26T17:01
tags:
  - Java
  - Todo
---
# Concept :
- Apache Log4j là 1 thư viện dược cung cấp bởi Apache hỗ trợ ghi log được viết bằng ngôn ngữ Java.
- Thread safe.

# Structure :
- Logger :  chịu trách nhiệm thu thập thông tin log.
- Appender : chịu trách nhiệm ghi log tới các vị trí đã được cấu hình. Có nhiều loại Appender.
- Layout : chịu trách nhiệm format kêt quả log. Có nhiều loại Layout.
	
	>![[Pasted image 20240226161708.png]]

# Log Level :
- Log nên được phân loại tùy theo mục đích sử dụng, theo level :
	- ***TRACE*** : Được sử dụng để ghi lại các thông điệp chi tiết nhất, thường là những sự kiện rất nhỏ hoặc chi tiết trong quá trình thực thi của chương trình. Thường được sử dụng để debug hoặc tìm kiếm sự cố trong mã nguồn.
	- ***DEBUG*** : các thông tin dùng để debug, chúng ta có thể bật tắt log này dựa vào mode của application.
	- ***INFO*** : các thông tin mà bạn muốn ghi nhận thêm trong quá trình hoạt động của hệ thống. VD : Số lượng request, status, duration, ... để biết traffic của hệ thống thê nào.
	- ***WARN*** : log các thông tin cảnh báo của chương trình.
	- ***ERROR*** : các lỗi khi chạy chương trình sẽ được log. CỐ gắng log toàn bộ thông tin liên quan nhiều nhất có thể reproduce lại được mà tốn ít thời gian nhất.
	- ***FATAL*** : log các lỗi nghiêm trọng xảy ra trong chương trình, có thể làm cho chương trình không thể sử dụng được nữa.
	- ***OFF *** :  đây là cấp độ cao nhất, được sử dụng khi chúng ra không muốn log bất kỳ thông tin nào nữa.


- Độ ưu tiên của các cấp độ log từ thấp đến cao :
> TRACE < DEBUG < INFO < WARN < ERROR < FATAL < OFF

