---
created: 2024-02-25T11:30
updated: 2023-11-14T10:10
tags:
  - Java
---
## Definition:
- **Stream**: là một trình bao bọc xung quanh nguồn dữ liệu, cho phép thực hiện các thao tác hàng loạt trên dữ liệu một cách thuận tiện nhờ các operation.
- Nó không lưu trữ và thực hiện bất kỳ thay đổi nào đối với nguồn dữ liệu cơ bản, thay vào đó là thêm các hỗ trợ dạng chức năng trên các đường dẫn dữ liệu.
- Stream được thiết kế để làm việc được với biểu thức `Lamda`.
- Interface Stream có thể được khởi tạo bằng cách gọi phương thức .stream() có trong các Collections.
## Stream Processing Phases:
- Xử lý các phần tử trong stream sẽ được thực hiện trong hai giai đoạn: Configuration và Processing.
	- Configuration: stream được cấu hình, thực ra là trải qua quá trình lọc và ánh xạ các phần tử.
	- Processing: xử lý bao gồm làm một việc gì đó cho các phần tử trong Collection.
- **Intermediate Operation**: là các method của stream, các method này sẽ return một stream khác và có thể được tận dụng để chain lại với nhau (nối các operation trung gian).
	- Mỗi operation sẽ có param là functional Interface để thực hiện phép biến đổi tương ứng

## Stream methods:
- **map**(): Biến đổi từng phần tử trong stream thông qua các hàm áp dụng cho từng phần tử trong stream và trả về một stream các giá trị (đây là bản chất cốt lõi của Java streaming API).
- **reduce():** giảm số lượng trong Stream thành một phần tử duy nhất(Không nhất thiết cùng class.
- **limit**(n): giới hạn bớt xuống n phần tử.
- **skip**(n): bỏ qua n phần tử đầu tiên.
- **distinct**(): loại bỏ các phần tử trùng nhau và chỉ giữ lại các phần tử riêng biệt.
- **sorted**(): sắp xếp các phần tử.
- **takeWhile**(): tiếp tục xử lý các phần tử khi điều kiện còn đúng, sai thì dừng lại.
- **dropWhile**(): tiếp tục bỏ qua element nếu điều kiện đúng, nếu sai thì toàn bộ phần còn lại sẽ được giữ lại.
- **filter**(): lọc phần tử theo `Predicate interface` ( chỉ có một tham số duy nhất và trả về kiểu dữ liệu là boolean).
- **collect**(): khi phương thức này gọi, filter() hay map() sẽ được diễn ra trước nó và kết quả của những hành động sẽ được thu thập sang một Collection khác.
- **min**() và **max**(): xử lý các phần tử trong stream và trả về kết quả giá trị lớn nhất (nhỏ nhất), kết quả trả về sẽ là một Optional Object nên có thể thực hiện .get() để lấy giá trị bằng không giá trị là null.
- **count**(): đếm số lượng phần tử trong collection.

> ![Exported image](Exported%20image%2020240225113028-3.png)  

## Parallel Stream:
- (luồng song song): cho phép thực hiện code một cách song song trong một cores riêng biệt. Kết quả cuối cùng là sự trộn lẫn của từng kết quả.
	[https://www.baeldung.com/java-when-to-use-parallel-stream](https://www.baeldung.com/java-when-to-use-parallel-stream)