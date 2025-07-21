- CPU-I/O Burst Cycle(Chu kỳ sử dụng CPU-I/O: Quá trình thực hiện Process luôn chứ một chu kỳ thực hiện của CPU và chu kỳ chờ của I/O, luân phiên nhau.
- Sự phân phối của CPU giúp lựa chọn giải thuật lập lịch của CPU.
  
- **CPU-Scheduler(Trình lập lịch CPU):**
- Khi CPU rỗi, HDH cần chọn trong số các Process ở trạng thái Ready trong bộ nhớ và phân phối CPU cho một trong số đó.
- Process được thực hiện bởi _Short-Term-Scheduler_.
- Các quyết định lập lịch CPU được xảy ra khi một Process:

1. Chuyển từ _Running_ sang _Waiting_ (I/O request).

2. Chuyển từ Running sang _Ready_ (Khi 1 Interrupt xuất hiện).

3. Chuyển từ _Waiting_ sang _Ready_ (I/0 hoàn thành).

- **Nonpreemptive/preemtive(Độc quyền/Không độ quyền):**
- Lập lịch CPU khi (1) va (4) là không được ưu tiên trước(nonpreemtive)-độc quyền:

+ Buộc phải chọn 1 Process mới để thực hiện.

+ Process được phân phối CPU sẽ chiếm hữu đến khi Terminated hoặc chuyển sang Waiting.

+ Các Process không sẵn sàng nhường điều khiển của CPU.

  
- Lập lịch CPU khi (2) và (3) là được ưu tiên trước(Preemtive)-Không độc quyền.

+ Khi (2): Process giải phóng CPU cần phải chọn Process kế tiếp.

+ Khi (3): Process có thể đẩy Process khác để dành điều khiển CPU.

  
- **Dispatcher(Trình điều vận):**
- Môdun Dispatcher trao quyền điều khiển CPU cho Process được chọn bởi trình lập lịch CPU:

+ Chuyển ngữ cảnh.

+ Chuyển sang UserMode.

+ Nhảy tới vị trí thích hợp trong chương trình của người sử dụng để khởi động lại chương trình đó.

- Dispatch-latency: thời gian cần thiết để trình điều vận dừng 1 Process và khởi động 1 Process khác chạy.

  

4. _Terminated_.

![Exported image](Exported%20image%2020240225092721-0.png)  
  
  
  

1. **Tiêu chuẩn lập lịch:**
2. CPU-utilization(tận dụng): giữ cho CPU càng bận càng tốt.
3. Throughtput(thông lượng tối đa): số Process được hoàn thành trong một đơn vị thời gian.
4. TurnAround-Time: tổng t/g 1 Process = t/g chờ đưa vào bộ nhớ + t/g chờ tại _Ready-queue_ + t/g thực hiện bởi CPU + t/g thực hiện vào-ra.
5. Waiting-Time: thời gian mà một Process chờ trong _Ready-queue._
6. Response-Time.

  

1. **Xác định thời gian chờ kế tiếp:**
![Exported image](Exported%20image%2020240225092721-1.png)  
4. **MultiProcessor(Lập lịch đa vi xử l****ý****)**:

  
![Exported image](Exported%20image%2020240225092721-2.png)  

1. **Realtime(Lập lịch thời gian th****ực****)**:

![Exported image](Exported%20image%2020240225092721-3.png)  

1. **Lựa chọn giải thu****ật** **lập lịch**: Lựa chọn giải thuật lập lịch CPU nào cho hệ thống cụ thể
  
3. **Các giải thuật lập lịch:**
4. **Fi****rst-Come, First-Served(FCFS)**: Không ưu tiên, Process nào yêu cầu CPU trước sẽ được phân phối CPU trước.
  
6. **Shorted-Job-First(SJF)**: Thời gian sử dụng CPU tiếp sau của nó được sử dụng để lập lịch các Process với thời gian đợi ngắn nhất.
7. Hai phương pháp Non-Preemptive(không ưu tiên trước) và Preemtive(ưu tiên trước).

+ Non-Preemptive: không nhường cho tiến trình khác cho đến khi nó Terminated.

+ Preemtive: nếu 1 Process đến có thời gian sử dụng CPU ngắn hơn thời gian còn lại của Process đang thực hiện thì ưu tiên Process mới đến. Phương pháp này còn gọi là _Shortest-Remaining-Time-First(SRTF)_.

-> SJF là tối ưu - cho thời gian chờ đợi TB của các Process là nhỏ nhất.

11. **Priority(Lập lịch ưu tiên)**: Mỗi Process được gắn một số ưu tiên(số nguyên) và CPU được phân phối cho tiến trình có mức ưu tiên cao nhất(có số ưu tiên nhỏ nhất).
12. Hai phương pháp Non-Preemptive(không ưu tiên trước) và Preemtive(ưu tiên trước).
13. Vấn đề: những Process có mức ưu tiên thấp có thể không bao giờ được thực hiện (_starvation_) -> Aging: ký thuật tăng mức ưu tiên của các Process chờ đợi lâu trong hệ thống. (VD: Sau 1-20p giảm số ưu tiên 1 lần).
14. **Round-Robin(RR**): Mỗi tiến trình được sử dụng một lượng nhỏ thời gian của CPU (time-quantum), thường là 10-100ms. Sau thời gian thực hiện q thì Process được đưa vào cuối của _Ready-queue_.
15. Ready-queue được tổ chức dưới dạng FCFS.
16. Nếu Process còn thời gian sd CPU < p thì Process sẽ giải phóng CPU khi _Terninated_ và không có mặt trong _Ready-queue_, trình lập lịch sẽ chọn Process kế tiếp trong Ready-queue. Nếu Process còn thời gian sd > p thì Timer sẽ đếm ngược về 0 gây ngắt HDH. Việc chuyển ngữ cảnh được thực hiện để chuyển điều khiển CPU cho Process ở đầu hàng đợi, Process hiện tại được đưa xuống cuối _ready-queue_.
17. **MultiLevel-Queue(Lập lịch hàng đợi đa m****ức****)**: Chia Queue thành nhiều queue, các Process cùng Queue có cùng độ ưu tiên.
18. Phổ biến:

+ Foreground: chứa những Process ảnh hưởng lẫn nhau(_Iteractive-Process_), thường dùng giải thuật RR.

+ Background: chứa Process bó(_Batch-Process_), thường dùng giải thuật FCFS.

  
22. Phải có sự ưu tiên giữa các Queue, mỗi Queue nhận được một thời gian CPU nào đó mà nó có thể dùng để lập lịch các Process của nó.

VD: 80% cho forground và 20% cho background-queue.

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092721-4.png)|![Exported image](Exported%20image%2020240225092721-5.png)|

  
26. Process có mức độ ưu tiên cao hơn khi vào Queue không ảnh hưởng đến Process đang chạy có mức độ ưu tiên thấp hơn.
27. Hạn chế:

+ Process trong Queue có độ ưu tiên thấp hơn chỉ có thể chạy khi Queue có mức độ ưu tiên cao hơn rỗng.

-> Process trong Queue có mức ưu tiên thấp có thể bị _Starvation_.

+ Process không thể di chuyển giữa các Queue.

  
32. **MultiLevel-Feedback-Queue(Lập lịch hàng đợi phản hồi đa m****ức****)**: Cho phép Process sử dụng nhiều _CPU-Burst_ có thể di chuyển từ Queue có độ ưu tiên cao hơn xuống Queue có độ ưu tiên thấp hơn.
  
34. **Lottery(Lập lịch sổ xố)**: Phát hành một vé số và phân phối cho các Process trong hệ thống. Đến thời điểm ra quyết định điều phối, sẽ tiến hành chọn một vé để được nhận CPU.

![Exported image](Exported%20image%2020240225092721-6.png)  

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092721-7.png) ![Exported image](Exported%20image%2020240225092721-8.png)|![Exported image](Exported%20image%2020240225092721-9.png)|

  
  

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092721-10.png)|![Exported image](Exported%20image%2020240225092721-11.png)|

  
  

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092721-12.png)|![Exported image](Exported%20image%2020240225092721-13.png)|

  
  
![Exported image](Exported%20image%2020240225092721-14.png)  
  
  
  
![Exported image](Exported%20image%2020240225092721-15.png)