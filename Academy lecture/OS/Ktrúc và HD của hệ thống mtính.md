- Mỗi khi khởi động máy tính thì phải thực hiện khởi động lại HDH, bao gồm cả các gói **service** (là các phần mềm bên ngoài được đóng gói) được chạy theo sắp xếp của người lập trình gọi là thuật toán.
  
- **Kiến trúc phần cứ****ng** **hệ thống máy tính hiện đại:**
- Bao gồm 3 khối: khối CPU, khối Memory(bộ nhớ chính: RAM, ROM), khối I/O.
- Các khối giao tiếp với nhau thông qua hệ thống 'ngắt'.
- CPU: có tốc độ xử lý tính toán cực kỳ nhanh.
- Khối Memory: khác nhau qua từng thế hệ ra đời(DDRAM4,DDRAM3,…) cự thể là dung lượng lưu trữ tăng và tốc độ xử lý cao (chậm hơn với CPU).
- Khối I/O: do tốc độ thao tác của con người rất chậm so với máy tính nên toàn bộ những dữ liệu sẽ được lưu tạm thời vào **localBuffer**(đệm dữ liệu) đến khi nào đủ để xử lý thì sẽ gửi cho CPU tiến hành xử lý.
- **Hoạt động của Hệ thống máy tính:**
- **Cơ chế ngắt (Interrupt)**: Khi thiết bị ngoại vi (I/O) có yêu cầu thì gửi yêu cầu ngắt đến CPU để xử lý, CPU ngừng công việc hiện tại để xử lý ngắt xong quay lại công việc ban đầu.
- Hệ thống hoạt động như một **I****nterupt driven**(quá trình điều khiển ngắt), mã lệnh của nó chỉ được gọi khi ngắt xuất hiện.
- **Interupt service routine**(Bảng vector ngắt - chứa địa chỉ của tất cả chương trình phục vụ ngắt) được thực thi bởi vi điều khiển hoặc CPU, chịu trách nhiệm thực hiện các ngắt ngắt chuyển điều khiển cho chương trình phục vụ ngắt thông qua **Interrupt vector**(vector ngắt).
- **Interrupt architecture** (Kiến trúc ngắt) phải lưu địa chỉ của lệnh bị ngắt, các ngắt đến bị **Disabled**(vô hiệu) trong khi một ngắt đang thực hiện để tránh bị **Lost interrupt** (mất ngắt).
- Có thứ tự ưu tiên cho hệ thống ngắt thông qua quy ước ở các đường ngắt-có IRQ càng thấp thì ưu tiên càng cao (ở Window xem trong **DeviceManager**).
- **Trap (**Bẫy lỗi) là ngắt mềm gây ra bởi lỗi hoặc do yêu cầu người dùng.
- Để hệ thống duy trì trạng thái của CPU thì phải thực hiện lưu giữ nội dung thanh ghi, bộ đếm chương trình(**PC-Program Counter**) và địa chỉ của lệnh ngắt.
- Phục vụ ngắt xong thì khôi phục lại ngữ cảnh trước ngắt.
- Phân loại ngắt:
- **Cơ chế Polling**: CPU thăm dò các bộ phận xung quanh (Display, KeyBoard, Printer, NIC, I/O devices,…) xem có bộ phận nào cần thực hiện hành động nào không(thực hiện xoay vòng - **polling**). Cho nên thời gian phục vụ thiết bị là ít hơn nhiều so với thời gian thăm dò.
- **Driver**: là chương trình điều khiển thiết bị ngoại vi(I/O) đã được viết sẵn, chỉ tương thích với hệ điều hành mà nó hỗ trợ, giúp giao tiếp giữa thiết bị ngoại vi với máy tính. Các ngoại vi đều có tốc độ xử lý khác nhau nên Driver cũng giúp đồng bộ cách thức hoạt động của thiết bị trong máy tính.
- Hoạt động: dữ liệu được trao đổi thông qua cổng I/O.
    
    - CPU ghi byte DL vào thanh ghi DL, _thiết lập 1 bit_ của thanh ghi điều khiển để _báo hiệu cho module điều khiển I/O_ -> _Module điều khiển I/O đọc byte DL, xóa bit thiết lập_ của thanh ghi điều khiển -> _CPU tiếp tục đọc byte DL kế ti__ếp_(Module điều khiển I/O không gây ngắt khi xong mà CPU sẽ thực hiện xoay vòng để kiểm tra trạng thái thiết bị).
      
    

  
![Exported image](Exported%20image%2020240225092714-0.png)

![Exported image](Exported%20image%2020240225092714-1.png)

_Mô hình trừu tượng_

  
![Exported image](Exported%20image%2020240225092714-2.png) ![Exported image](Exported%20image%2020240225092714-3.png)