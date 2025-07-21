1. **Critcal-Region**(Đoạn găng): Là đoạn code có khả năng mâu thuẫn khi truy xuất tài nguyên chung. Hdh cần các giải pháp đồng bộ để giải quyết vấn đề độc quyền truy xuất: Quyết định xem Process nào được vào đoạn găng, còn lại các Process khác không thể vào đoạn găng.
  
3. **Các giải pháp Busy-Waiting:**
4. **Giải pháp phần mềm:**
    
    1. **Simaphore**(biến cờ hiệu): Các Process chia sẻ chung một biến làm chốt(lock) với giá trị khởi tạo là 0. Một Process muốn vào đoạn găng thì cần kiểm tra giá trị của biến lock này bằng 0 thì được phép vào và đặt biến thành 1. Còn ngược lại thì không được vào và chờ đến khi biến này thành 0 lại.
    ![Exported image](Exported%20image%2020240225092719-0.png)
    
    - Vấn đề: Khi Process 1 vào đoạn găng chưa kịp đặt lock=1 thì đã hết thời gian nên phải nhường lại CPU cho Process 2; Process 2 vào và đặt lock=1 nhưng chưa kịp hoàn thành đoạn găng thì phải nhường lại CPU cho Process 1 -> TH cả 2 Process cùng trong đoạn găng.
      
    - **Alternate-testing**(Kiểm tra luân phiên): Sử dụng biến dùng chung Turn=0 lúc khởi đầu để Process0 được vào đoặn găng, Turn=1 thì Process1 được vào đoạn găng.
    ![Exported image](Exported%20image%2020240225092719-1.png)
    
    - Vấn đề: Khi Process0 vào đoạn găng đặt Turn=1 rồi phải nhường lại CPU cho Process1 và muốn nhanh chóng quay lại đoạn găng nhưng Process1 thực hiện hết tgian CPU mà vẫn chưa vào đoạn găng thì lúc này biến Turn=1 không đổi nên Process0 không thể vào. -> 1 Process bị ngăn vào đoạn găng bởi Process ngoài đoạn găng.
    - Vấn đề gặp phải khi 1 Process muốn vào đoạn găng liên tục còn Process còn lại thì không cần thiết lắm trong khi đó số lần vào đoạn găng của hai Process là cân bằng.
    
    1. **Peterson**:
    ![Exported image](Exported%20image%2020240225092719-2.png)
    
    - Triển Khai:
    
    - Ngăn chặn được tình trạng mâu thuẫn: Process1 vào được đoạn găng khi và chỉ khi turn=1 hoặc interesse[j]=FALSE. -> Không thể cho nhiều Process vào đoạn găng.
  
6. **Giải pháp có sự hỗ trợ phần cứng:**
    
    1. **Cấm ngắt**: Cho phép Process cấm tất cả các ngắt trước khi vào đoạn găng và phục hồi ngắt khi ra khỏi đoạn găng.
    2. Khi đó ngắt đồng hồ cũng không thể xảy ra do vậy hệ thống không thể tạm dừng Process đang xử lý để cấp phát CPU cho tiến trình khác -> Không thể có tranh chấp.
    3. Hạn chế:￼+ Không được ưa chuộng vì việc cho phép User-Process được thực hiện cấm ngắt là thiếu thận trọng.
    
    + Trong hệ thống Multi-Processor thì việc cấm ngắt trên 1 CPU không ảnh hưởng đến các Process ở CPU còn lại nên các Process đó vẫn có thể truy xuất đến đoạn găng.
    
    1. **Test&Set**: Tập lệnh máy có thêm một chỉ thị đặc biệt cho phép kiểm tra và cập nhật nội dung một vùng nhớ trong một THAO TÁC NGUYÊN TỬ gọi là chỉ thị _Test-And-SetLock(TSL)._
    2. Nếu có hai chỉ thị TSL xử lý đồng thời (trên CPU khác nhau) chúng sẽ được xử lý tuần tự.
    3. Giải pháp truy xuất độc quyền ở đây là dùng biến dùng chung lock, khởi tạo là False và chỉ khi lock==FALSE thì Process mới có thể vào đoạn găng.
      
    

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092719-3.png)|![Exported image](Exported%20image%2020240225092719-4.png)|

- Hạn chế:

+ Giảm nhẹ công việc lập trình nhưng việc cài đặt TSL như một lệnh máy là không hề đơn giản.

+ Khi có nhiềui CPU, việc điều phối TSL cho từng CPU gặp khó khăn.

  
- **KL về Busy-waiting**:
- Tất cả các giải pháp trong nhóm này đều phải thực hiện 1 vòng lập để kiểm tra xem có được phép vào đoạn găng hay không, đương nhiên việc kiểm tra vẫn tốn CPU để check liên tục.

-> _Busy-Waiting(Bận vì chờ), xu hướng giải quyết vấn đề đồng bộ hóa là tránh các giải pháp Busy-waiting_.

  
10. **Các giải pháp SLEEP and WAKEUP**: HDH sử dụng hai thủ tục Sleep và WakeUp trong đó:
    
    - _Sleep_: là lời gọi hệ thống có tác dụng làm dừng hoạt động của Process bằng cách khiến Process chuyển sang tt Waiting.
    - _WakeUp_: là lời gọi hệ thống nhận tham số truyền vào duy nhất chính là Process cần được tái kích hoạt bằng cách trả về tt Ready.
11. Khi 1 Process chưa đủ đk để vào đoạn găng thì sẽ thực hiện Sleep đến khi có Process thực hiện xong đoạn găng rồi gọi đến hệ thống bằng lệnh WakeUp tạo cơ hội cho Process khác được vào đoạn găng.
![Exported image](Exported%20image%2020240225092719-5.png)  
14. **Đèn báo Simaphore(Dijiktra đề xuất)**: Là một biến tài nguyên S được phục vụ điều độ.(VD: 3 máy in, 10 chỗ trống trong buffer)
15. Simaphore Mutex hay còn được gọi là Simaphore nhị phân.
16. Chỉ có thể thay đổi giá trị bởi 2 thao tác cơ bản P và V:
![Exported image](Exported%20image%2020240225092719-6.png)

1. **Điều độ thứ tự thực hiện bên trong các Process: HỦY BỎ CHỜ ĐỢI TÍCH CỰC**
2. Hai Process thực hiện đồng thời: Yêu cầu S2 thực hiện chỉ khi S1 thực hiện xong(P1 chứa S1, P2 chứ S2).
3. Đèn báo Synch khởi tạo 0.

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092719-7.png)  <br><br>-> _Việc điều độ đèn báo Synch giúp tránh xảy ra tình trạng CPU hoạt động vô ích_.|![Exported image](Exported%20image%2020240225092719-8.png)|

  
6. **Cài đặt đèn báo**:
7. S.value khởi tạo 1.
8. S.Ptr khởi tạo Null.
![Exported image](Exported%20image%2020240225092719-9.png)

1. **Hạn chế**:
2. Các phép xử lý P(S) và V(S) không phân chia được và bản thân cũng là tài nguyên găng nên cũng cần phải được xử lý điều độ.
  
4. Hệ thống nhiều VXL thì cấm ngắt trên 1 VXL không ảnh hưởng đến các VXL khác.

1. **Đối tượng Semaphore trong win32**:
![Exported image](Exported%20image%2020240225092719-10.png)

  
22. **Monitor:**

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092719-11.png)|![Exported image](Exported%20image%2020240225092719-12.png)|

1. **Biến điều kiện:**
![Exported image](Exported%20image%2020240225092719-13.png)  
4. **Sử dụng chung 1 tài nguyên:**
5. Process sẽ thực hiện lời gọi Acquire() xem tài nguyên có bận hay không. Nếu tài nguyên bận(Busy=true) thì Process đó sẽ thực hiện wait. Cho đến khi Process 'sử dụng tài nguyên' xong rồi thực hiện lời gọi Release() để giải phóng tài nguyên(Busy=false) và đánh thức Process đang bị khóa.
![Exported image](Exported%20image%2020240225092719-14.png)  
8. **Một số bài toán đồng bộ Process:**
9. Producer-Consumer(Bounded Buffer Problem) 1 : Counter có giá trị khởi tạo 0, khi thực hiện thêm phần tử mới vào Buffer sẽ đồng thời dịch IN để trỏ vào vùng nhớ tiếp theo(% để quay đầu lại), khi Counter=1 sẽ thực hiện đánh thức Consumer để thực hiện tiêu thụ, cứ như thế cho đến khi Producer sản xuất đầy Buffer thì dừng. Khi Counter==SIZE-1 thì Consumer lại tiếp tục thực hiện wake-up để Producer sản xuất.
10. Producer-Consumer(Bounded Buffer Problem) 2: Dùng một đèn báo Mutex để điều độ biến Counter. Có gtri khởi tạo =1.
11. Producer-Consumer(Bounded Buffer Problem) 3: Sử dụng đèn báo Full, Empty được khởi tạo với Full=0: số phần tử trong hòm thư; Empty=Buffer_size: số chỗ trống trong hòm thư.
12. Producer-Consumer(Bounded Buffer Problem) 4: Dùng đèn báo thứ 3(mutex<-1) để đồng bộ các Process cùng loại.

+ Wait(empty): kiểm tra xem Buffer còn chỗ trống để đặt thêm không.

![Exported image](Exported%20image%2020240225092719-15.png)  
  
  
  
  
  
![Exported image](Exported%20image%2020240225092719-16.png)  
  
  
  
  
  
  
  
![Exported image](Exported%20image%2020240225092719-17.png)  
  
  
![Exported image](Exported%20image%2020240225092719-18.png)  
  
  
  
  
  
![Exported image](Exported%20image%2020240225092719-19.png)  
![Exported image](Exported%20image%2020240225092719-20.png)

-> Vấn đề: Khi Consumer kiểm tra Counter==0 mà đúng nhưng chưa kịp thực hiện block() đã bị khóa rồi Producer được vào running đến cuối cùng thực hiện wakeUp() nhưng do Consumer chưa bị block nên wakeUp() này bị bỏ qua. Consumer sau đó mới được thực hiện lệnh block() rồi bị dừng tạm thời. Producer cứ tiếp tực sản xuất cho đến khi đầy thì tự động bị block()(do counter==SIZE). Giờ cả hai đều bị block() nên không thể thực hiện được gì nữa.

  
![Exported image](Exported%20image%2020240225092719-21.png)

-> Vấn đề: Khi có nhiều Producers và Consumers, Các biến IN và OUT trở thành tài nguyên găng.

  

+ Wait(mutex): 1 Process lấy quyền được thay đổi giá trị Counter(thực thi vùng găng).

![Exported image](Exported%20image%2020240225092719-22.png)