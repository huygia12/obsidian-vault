---
created: 2024-02-25T11:31
updated: 2023-07-25T14:08
---
- **Thread**(luồng) : là một tiến trình con(sub-process). Một đơn bị xử lý nhỏ nhất của máy tính có thể thực hiện một công việc riêng biệt. Trong java các nguồn được quản lý bởi máy ảo `JVM`.
- **Multi-Thread**(Đa luồng): là một tiến trình thực hiện nhiều luồng đồng thời. Một ứng dụng Java ngoài luồng chính có thể có các luồng khác thực thi đồng thời làm ứng dụng chạy nhanh và hiệu quả.
- **Multi-tasking**: là khả năng chạy đồng thời một hoặc nhiều chương trình cùng 1 lúc trên một hệ điều hành. Hệ điều hành quản lý bằng cách sắp xếp lịch phù hợp cho từng chương trình. Có thể đạt được bằng hai cách:
	- **Dựa trên Đơn tiến trình - Đa tiến trình:** mỗi tiến trình trình phân bổ vùng nhớ riêng biệt; tiến trình là nặng; sự giao tiếp giữa các tiến trình có chi phí cao; chuyển đổi từ tiến trình này sang tiến trình khác đòi hỏi thời gian để đăng ký việc lưu và tải các bản đồ bộ nhớ, các danh sách cập nhật,…
		- Giải thuật `Round Robin`: sắp xếp cách tiến trình thành vòng tròn rồi hệ thống lập lịch để thực hiện luân phiên nhau xử lý lệnh cho chương trình.
	- **Dựa trên luồng - Đa luồng:** các luồng chia sẻ không gian địa chỉ ô nhớ giống nhau; luồng là nhẹ; sự giao tiếp giữa các luồng có chi phí thấp.
  
- **Ưu điểm đa luồng** :
	- Không chặn người dùng vì các luồng là độc lập và bạn có thể thực hiện nhiều công việc cùng 1 lúc.
	- Có thể chia sẻ chung 1 tài nguyên trong quá trình chạy ở mỗi luồng nhưng thực hiện một cách độc lập.
	- Nếu ngoại lệ xảy ra thì không ảnh hưởng đến luồng khác.
	- Có thể thực hiện nhiều hoạt động với nhau để tiết kiệm thời gian(tách ra làm nhiều luồng trong 1 ứng dụng).
- **Nhược điểm đa luồng:**
	- Càng nhiều luồng thì xử lý phức tạp.
	- Vấn đề tranh chấp bộ nhớ, đồng bộ dữ liệu phức tạp.
	- Phát hiện và tránh các luồng chết(dead lock), chạy mà không làm gì.
  
![Exported image](Exported%20image%2020240225113110-0.png)  
- **Cách tạo luồng trong java**: Tạo luồng bằng hai cách là kế thừa lớp Thread hoặc implements interface Runnable.
![Exported image](Exported%20image%2020240225113110-1.png)  
- **Các phương thức thường được sử dụng**:
![Exported image](Exported%20image%2020240225113110-2.png)  
![Exported image](Exported%20image%2020240225113110-3.png)  
- **Đồng bộ Thread (Synchronized)****:** **đồng bộ các luồng để tại một thời điểm chỉ có một luồng tác động lên dữ liệu.**
- Đồng bộ phương thức(method): thêm Synchronized vào sau access Modifier trong phương thức
- Nhiều luồng thao tác đến phương thức sẽ được thực thi tuần tự: các luồng đến sau sẽ được đẩy vào Queue để đợt lượt.
  
- Đồng bộ Khối(block): thêm synchronized(tài nguyên) vào trong hàm để đẩy các luồng có sử dụng tài nguyên vào Queue.
- Lưu ý cần phải sử dụng thêm : notifyAll và wait để hàm luồng được xử lý lần lượt. Luồng không tự động kết thúc nên phải gọi stop nếu không sẽ bị deadLock.

  
![Exported image](Exported%20image%2020240225113110-4.png)  
  
  
  
  
  
  

> [!warning] Lưu ý trong lập trình đa luồng:
>#### **Race condition:**
> -  Tình trạng phát sinh khi nhiều luồng thực hiện song song trên cùng một đối tượng mà không có sự đồng bộ hóa thích hợp.
> #### Phân biệt Wait và Sleep :
> - Wait : là một instance method được sử dụng để đồng bộ hóa, giao tiếp giữa các luông; chỉ được gọi trong monitor object( một synchronized Block truy cập vào các object được sử dụng bởi nhiều Thread); khi được gọi thì luồng sẽ rơi vào trạng thái chờ cho đến khi một luồng khác đánh thức nó hoặc tự đánh thức sau một thời gian chỉ định.￼
> - Sleep : là một static Method có thể gọi ở bất cứ đâu; dùng để quản lý thời gian của một Thread; tạm dừng luồng hiện tại cho đến khi được đanhs thức bởi khoảng thời gian chỉ định.
> #### Hàm run()
>  - Khi gọi phương thức start của Thread nó sẽ tạo luồng mới rồi thực thi code trong run() nhưng nếu gọi trực tiếp run() thì sẽ không quan tâm đến việc tạo luồng rồi thực thi mã trên cùng một luồng được gọi, lúc này run() sẽ không khác một phương thức bình thường và không thể tận dụng được đa luồng.

  

