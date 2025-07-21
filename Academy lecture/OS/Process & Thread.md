- **Tiến trình (Process)****:** Là một chương trình đang được thực thi, cần được cung cấp đầy đủ tài nguyên cần thiết, được CPU tiếp nhận và thực hiện; sở hữu một con trỏ lệnh, tập các thanh ghi và các biến.
- Tiến trình khác với chương trình:

+ Chương trình: là một thực thể thụ động chứa câu lệnh và dữ liệu đi kèm để tiến hành một tác vụ, chưa được nạp vào Ram(chưa được đưa vào chờ để CPU lập lịch xử lý).

+ Tiến trình : là một thực thể hoạt động, được cấp phát toàn bộ tài nguyên cần thiết để thực hiện chạy, được nạp vào trong Ram(còn chờ đến CPU để được xử lý).

  
- Một tiến trình gồm:
    
    1. ***Các trạng thái của tiến tr****ình****:** được xác định bởi hoạt động của tiến trình tại thời điểm đó. Trong quá trình đó thì tiến trình có thể thay đổi trạng thái do các nguyên nhân:
    ![Exported image](Exported%20image%2020240225092704-0.png)  
    ![Exported image](Exported%20image%2020240225092704-1.png)
    
    1. ***PCB**(Khối điều khiển tiến trình)
    ![Exported image](Exported%20image%2020240225092704-2.png)
    
    - PCB quyết định tiến trình nào được sử dụng CPU và căn cứ vào nội dung của PCB mà giải phóng CPU ảo(là CPU logic được phân phối cho toàn bộ tiến trình, tốc độ << CPU thực).
      
    
    4. *******CPU** **chuyển giữa các tiến tr****ình**:
    5. **Đặc điểm tiến trình**: các tiến trình phân cấp theo một số tiêu chuẩn đánh giá thông qua _thời gian sử dụng CPU_(để tiến hành lập lịch), _thời gian còn lại tiến trình cần để hoàn t__ất_(giảm thiểu thời gian chờ đợi bằng cách cho các tiến trình có ít thời gian nhất để hoàn thành thực hiện trước.
    6. I/O bound process(tiến trình hướng I/O): thực hiện vào ra tốn nhiều thời gian, chiếm dụng CPU ngắn, cần chuyển ngữ cảnh thường xuyên khi bắt đầu và kết thúc I/O.
    7. CPU bound process(tiến trình hướng xử lý): sử dụng nhiều thời gian cho việc tính toán, chiếm CPU dài, chuyển ngữ cảnh thường xuyên tránh việc tiến trình ngăn tiến trình khác sử dụng CPU.
    8. Tiến trình xử lý theo lô: các tiến trình chiếm CPU trong khoảng thời gian như nhau(**quantum**-lượng tử thời gian).
      
      
    11. **Lập lịch tiến trình**: chạy nhiều tiến trình tại cùng một thời điểm để tối ưu hóa sử dụng CPU, người sử dụng có thể tương tác với chương trình khi nó đang chạy bằng việc chuyển CPU giữa các tiến trình càng thường xuyên càng tốt(**time-sharing**).
    12. Nguyên tắc: Chọn 1 tiến trình trong hàng đợi(trạng thái ready) có độ ưu tiên cao nhất, cần xem xét thời gian chờ đợi xử lý.
    13. HDH sử dụng **Ready-list** và **Waiting-list** để điều phối các tiến trình.
    14. Trình lập lịch: **Long-term-scheduler**(tiến trình từ vùng đệm bộ nhớ ngoài vào bộ nhớ trong-ready-list, không được sử dụng thường xuyên, tốc độ châm) và **Short-term-scheduler**(lập lịch CPU- lựa chọn tiến trình nên thực hiện rồi pp CPU, được sử dụng thg xuyên, tốc độ nhanh).
    
    1. **Hoạt động của tiến trình**: HDH cấp các thao tác sau trên một tiến trình
    2. Tạo lập tiến trình (create or new): tiến trình cha có thể tạo ra các tiến trình con(cây tiến trình) rồi phải phân phối bộ nhớ và tài nguyên(định danh cho tiến trình mới, đưa vào ds qly của hệ thống, xd độ ưu tiên, tạo PCB, cấp phát tài nguyên ban đầu).
    
    - Kết thúc tiến trình(destroy or terminal): sử dụng lời gọi hệ thống để yc HDH hủy bỏ, dữ liệu từ tiến trình con đến tiến trình cha(qua lệnh wait). Tiến trình cha có thể chấm dứt việc thực hiện tiến trình con(hầu hết các hệ điều hành không cho tiến trình con tồn tại khi tiến trình cha kết thúc).
    - Tạm dừng tiến trình: yêu cầu thêm tài nguyên(hoặc chờ sự kiện)
    - Tái kích hoạt- thay đổi độ ưu tiên: khi được đáp ứng yc (về tài nguyên, I/O) sẽ chuyển lại về trạng thái ready(không cần cấp phát lại tài nguyên). Tiến trình chỉ thay đổi độ ưu tiến khi có một tiến trình kích hoạt(sinh ra hoặc quay trở lại ready) hoặc có tiến trình từ running bị timeout về lại ready.
    
    1. **Các tiến trình hợp tác**:
    2. **Independent Process**(Tiến trình độc lập): không tác động hay chịu tác động của tiến trình khác.
    3. **Cooperating Process**(Tiến trình hợp tác): tiến trình có thể tác động hoặc chịu tác động từ tiến trình khác, _Producer Process_ tạo thông tin cho _Consumer Process_ tiêu thụ. Giúp _Information Sharing_, _Computation Speed-up_, _Modularity_, _Convience_(người sử dụng có thể cùng thực hiện soạn thảo, in ấn, biên dịch song song.
    
    1. ***Các tiến trình liên lạc**: các tiến trình có không gian địa chỉ riêng biệt, liên lạc bằng cơ chế cho HDH cung cấp phải đáp ứng được các vde:
    2. Các cơ chế liên lạc:
        
        - Mỗi tiến trình có một bảng biểu diễn các signal khác nhau với các trình xử lý signal(signal Handler) tương ứng với từng **tín hi****ệu**.
        - Signal có thể được gửi đi bởi: phần cứng; HDH gửi đến 1 tiến trình; tiến trình đến 1 tiến trình khác; người dùng(VD:Ctrl + F4 để ngắt xử lý tiến trình).
        - Tiến trình nhận Signal có thể bỏ qua, xử lý theo mặc định, hoặc xử lý theo cách đặc biệt.
        - Hạn chế: không đồng bộ(không biết trước khi nào tiến trình nhận đc signal); không biết sự kiện(tương ứng với signal) có thực sự xảy ra không; các tiến trình chỉ có thể thông báo cho nhau về một biến cố nào đó; không thể trao đổi DL bằng cơ chế này.
        
        - 1 Tiến trình kết nốt đến Pipe chỉ có thể thực hiện 1 thao tác đọc hoặc ghi.
        - Tiến trình chỉ được phép sd Pipe nó tạo ra hoặc được kế thừa từ Tiến trình cha.
        - HDH cung cấp lời gọi cho tiến trình Read/Write để đọc/ghi DL vào Pipe.
        - HDH đồng bộ hóa truy xuất Pipe nếu trong Pipe trống/đầy để đợi đến khi có DL truy xuất/có chỗ trống.
        - Là cơ chế liên lạc Unidirectional(liên lạc 1 chiều), một số HDH cho phép thiết lập 2 Pipe giữa 1 cặp tiến trình để tạo liên lạc 2 chiều(có thể bị DeadLock khi cả 2 Tiến trình đều thực hiện đọc/ghi trên các pipe đã đầy/trống).
        - Cơ chế cho phép truyền DL với cách thứuc không cấu trúc nhưng chỉ giới hạn kết nối 2 tiến trình có quan hệ cha-con, trên cùng máy tính.
        
        - DL chỉ là đặt vào 1 vùng nhớ dùng chung mà các tiến trình đều truy xuất được đến(không phải truyền DL).
        - Các Process link vùng nhớ đó vào không gian địa chỉ riêng của từng tiến trình(thao tác trên đó như vùng nhớ riêng).
        - Ưu điểm: Là cơ chế nhanh nhất khi muốn trao đổi DL.
        - Hạn chế: không biết DL truy cập là mới nhất hay không; DL có thể bị override bởi Process khác trước khi kịp truy xuất để đọc -> cần được bảo vệ bằng cơ chế sync thích hợp; Không thể áp dụng trong hệ phân tán.
        
        - HDH cung cấp hai hàm IPC(InterProcess-Communication) cơ bản: Send và Receive.
        - Hai Process muốn giao tiếp cần thiết lập _Communication-Link_ giữa chúng, trao đổi dưới dạng mesage, kết thúc trao đổi _Communication-Link_ bị huỷ bỏ.
        - Các thức thực hiện liên kết: liên lạc trực tiếp/gián tiếp, liên lạc đồng bộ/không đồng bộ.
        
        - VD: Socket 165.25.19.8:1625 có nghĩa là Port 1625 có địa chỉ IP 161.25.19.8.
        - Sự giao tiếp diễn ra giữa một cặp Socket: _Server-Socket_ được chọn và _Client-Socket_ được gán tự động.
    3. **Phân phố tài nguyên Process:**
    4. HDH quản lý nhiều loại tài nguyên khác nhau và đều cần một cơ chế cấp phát, chiến lược hiệu quả.
    5. Mặc dụ biểu diễn qua các cấu trúc DL khác nhau nhưng mỗi loại tài nguyên về cơ bản chứa đựng các thông tin:
        
        - Định danh tài nguyên: phân biệt tài nguyên.
        - Trạng thái tài nguyên: thông tin mô tả chi tiết tài nguyên(phần nào đã cấp phát cho tiến trình, phần nào còn sd được).
        - Hàng đợi: chứa danh sách những Process đang chờ được cấp phát tài nguyên.
        - Bộ cấp phát: là đoạn code đảm bảo nhiệm vụ cấp phát một tài nguyên đặc thù.
    6. Đảm bảo số lượng hợp lệ các Process truy cập đồng thời đến tài nguyên; Cấp phát tài nguyên cho Process trong khoảng thời gian delay có thể chấp nhận được; Tối ưu hóa sd tài nguyên.
    7. **Vấn đề**:
    8. Mỗi Process có một không gian địa chỉ và chỉ có một dòng xử lý.
    9. Muốn tăng tốc độ và sử dụng CPU cần nhiều dòng xử lý, chia sẻ chung một không gian địa chỉ.
      
    
- **Luồng(Thread)**: Là một dòng xử lý cơ bản trong hệ thống, sở hữu một con trỏ lệnh, tập các thanh ghi và vùng nhớ stack riêng.
- Phân biệt Process vs Thread:
    
    - Thread được coi là mức thấp hơn của Process, Process có thể có nhiều luồng.
    - Cơ bản Thread hoạt động song song như các Process nhưng lại cùng chia sẻ không gian địa chỉ chung(tiến trình hoàng toàn độc lập).
- Khi máy tính có nhiều CPU có thể thực hiện Thread cho cùng một công việc hay các công việc khác nhau. Nhưng khi chỉ có 1 CPU thì Thread được thực hiện luân phiên, không có Thread nào được chiếm ưu thế.
- Các Thread được lập lịch để thực hiện vì có Thread chờ một biến cố xảy ra, có Thread chờ kết thúc một công việc từ Thread khác.
- Thread bao gồm:
    
    - Thread ID(Mã Luồng).
    - PC(Bộ đếm chương trình).
    - Register-Set(Tập thanh ghi).
    - Stack(Ngăn xếp).
- Các Thread chia sẻ với nhau cùng một đoạn mã(Code), đoạn DL(Data) và các tài nguyên hệ thống khác như tệp mở, các tín hiệu.
    
    1. Phân loại Thread:
    2. Luồng nhân:
    
    + Kernel của HDH có thể được cài đặt để Thread thành dvi cơ sở sử dụng CPU. HDH sẽ phân phối CPU các luồng trong hệ thống -> Luồng mức nhân.
    
    + Kernel thực hiện tạo Thread, lập lịch và quản lý các Thread trong không gian Kernel -> Chậm hơn các User Thread.
    
    + Nếu một Thread thực hiện System-Call bị khóa, Kernel có thể lập lịch một Thread khác để thực hiện.
    
    + Trong môi trường MultiProcesser, Kernel có thể lập lịch các Thread trên các Processor khác nhau.
    
      
    8. User-Thread(Luồng mức người dùng):
    
    + Được hỗ trợ trêm Kernel và được thực hiện bởi thư viện luồng tại mức người sử dụng (User-Level).
    
    + Tạo Thread và thực hiện trong không gian người sử dụng -> User-Level Thread nhanh để tạo, quản lý.
    
    + Thread thuộc mức User-Mode sẽ được ánh xạ vào Thread hoặc Process mức Kernel để thực hiện.
    
    + Hạn chế: Khi Kernel là đơn luồng, nếu có q User-Level Thread thực hiện 1 System-Call bị khóa sẽ khiến cho cả Process đó bị khóa, mặc dù Process khác vẫn có thể chạy trong ứng dụng.
    
      
    14. Các mô hình MultiThread: nhiều HDH hỗ trợ cả UserThread và KernelThread thể thiện trong 3 mô hình multiThread phổ biến:
    15. _Many-to-one:_ Nhiều User-level-Thread được ánh xạ vào 1 Kernel Thread; Việc quản lý Thread được thực hiện trong không gian người dùng.
    16. One-to-one: Mỗi User-level-Thread được ánh xạ vào 1 Kernel-Thread; cho phép 1 Thread khác chạy ngay cả có 1 Thread tạo System-Call bị khóa; Cho phép các Thread chạy song song trên multiProcessor.
    17. Many-to-many: (n)User-level-Thread được ánh xạ vào (m)Kernel-Thread (m<=n); Người phát triển có thể tạo bao nhiêu user-level thread tùy ý, các kernel thread tương ứng có thể chạy song song trên multiprocessor; Khi 1 thread thực hiện 1 system call bị khóa, kernel có thể lập lịch 1 thread khác để thực hiện.
    ![Exported image](Exported%20image%2020240225092704-3.png)  
    

  
![Exported image](Exported%20image%2020240225092704-4.png)  
  
  
![Exported image](Exported%20image%2020240225092704-5.png)  
  
![Exported image](Exported%20image%2020240225092704-6.png)  
  
![Exported image](Exported%20image%2020240225092704-7.png)

_Idle_: thời gian nhàn rỗi, nghỉ chạy.

  
  
  
  
  
  
![Exported image](Exported%20image%2020240225092704-8.png)  
![Exported image](Exported%20image%2020240225092704-9.png)  
![Exported image](Exported%20image%2020240225092704-10.png)  
![Exported image](Exported%20image%2020240225092704-11.png)  
  
  

+ _Explicit-naming/Implicit-naming_(tường minh/tiềm ẩn - biết tiến trình nào đang chia sẻ thông tin với nó)

+ _Blocking/Non-blocking_(đồng bộ/không đồng bộ - nếu đồng bộ thị cần phải đợi thao tác liên lạc hoàn tất rồi mới xử lý cái khác)

+ Liên lạc giữa các tiến trình trong hệ thống tập trung và hệ thống phân tán.

+ _Signal_(Tín hiệu): còn được gọi là _Software-Interrupt_(ngắt mềm), dùng để thông báo một sự kiện(không thể dự đoán được khi nào xảy ra), mỗi signal tương ứng với một sự kiện đặc trưng.

+ _Pipe_(Đường ống): là kênh liên lạc trực tiếp một chiều giữa 2 tiến trình, DL xuất của tiến trình này được chuyển đến làm DL nhập của tiến trình kia dưới dạng 1 dòng các Byte(giới hạn 4096 ký tự) va được bảo toàn theo ntac FIFO.

+ _Shared-Memory_(Vùng nhớ chia sẻ): cho nhiều tiến trình cùng truy xuất đến 1 Shared-memory.

+ _Trao đổi thông điệp_: thông qua trao đổi thông điệp để giao tiếp và đồng bộ các hành động giữa các tiến trình mà không cần chia sẻ không gian địa chỉ chung.

+ _Sockets_: được định nghĩa là Endpoint for communication, xác định bởi địa chỉ IP và số hiệu cổng.

![Exported image](Exported%20image%2020240225092704-12.png)  
![Exported image](Exported%20image%2020240225092704-13.png)  
  
  
  

-> Nhanh nhưng Process dễ bị khóa; Các luồng không thể chạy song song trong các hệ thống MultiProcesser.

![Exported image](Exported%20image%2020240225092704-14.png)

-> Cần giới hạn số Thread được hỗ trợ bởi HDH.

![Exported image](Exported%20image%2020240225092704-15.png)  

Vd:UNIX

![Exported image](Exported%20image%2020240225092704-16.png)