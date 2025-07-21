- **Các khái niệm****:**
- **Kết nối địa chỉ****:**

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092707-0.png)|![Exported image](Exported%20image%2020240225092707-1.png)|

  
- Việc kết nối các lệnh, dữ liệu tới địa chỉ bộ nhớ có thể xảy ra 3 giai đoạn khác nhau:
  

|   |   |   |
|---|---|---|
|![Exported image](Exported%20image%2020240225092707-2.png)|![Exported image](Exported%20image%2020240225092707-3.png)|![Exported image](Exported%20image%2020240225092707-4.png)|

  
- **Physical-address-space & Logical-Address-space:**
- Khái niệm không gian địa chỉ logic (logical address space) được tách riêng với không gian địa chỉ vật lý (physical address space) để quản lý bộ nhớ thích hợp.
    
    - Logical address – được tạo ra bởi CPU, còn gọi là địa chỉ ảo (_virtual-address_).
    - Physical address – địa chỉ được nhận biết bởi đơn vị bộ nhớ (_memory-unit_).
- Các địa chỉ logic (ảo) và vật lý là như nhau trong các giai đoạn gắn kết địa chỉ _compile-time_ và _load-time_; chúng khác nhau trong _execution-time_.
  

- Là thiết bị phần cứng ánh xạ địa chỉ ảo tới địa chỉ vật lý.
- Trong lược đồ MMU, giá trị trong thanh ghi định vị (relocation register) được cộng với tất cả địa chỉ được sinh ra bởi tiến trình của người dùng tại thời điểm nó được gửi tới bộ nhớ.
- Chương trình của người dùng làm việc với các địa chỉ logic; nó không bao giờ nhận ra các địa chỉ vật lý thực.
  

- **Dynamic Loading(tải động)**: bản chẩt là những đoạn mã được sd nhiều trong các Process, nếu sd DLL thì không cần sao thành nhiều bản mà vẫn có thế dùng cho nhiều chương trình.
- Chương trình(routine) chỉ được nạp vào bộ nhớ khi nó được gọi.
- Sử dụng không gian bộ nhớ tốt hơn, Process không dùng đến thì không bao giờ được nạp.
- Hiệu quả:

+ Hữu ích trong trường hợp sl lớn mã cần xử lý hiếm khi xuất hiện.

+ Không yêu cầu sự hỗ trợ đặc biệt từ HDH, được thực hiện thông qua thiết kế chương trình.

  
- **Dynamic Liking**(DLL-Liên kết động):
- Việc lien kết hoãn lại đến Execution time.
- Stub: đoạn mã nhỏ, sd để định vị các chương trình thư viện cư trú trong bộ nhớ(memory-resident library routine) thích hợp.
- Khi cần thực hiện, Stub kiểm tra Routine(đoạn mã thường được dùng ở nhiều nơi) cần đến có trong bộ nhớ của Process: nếu chưa thì chương trình nạp Routine vào bộ nhớ; Nếu rồi thì Stub tự thay thế chính nó bởi địa chỉ của thường trình rồi thực hiện thường trình đó.
- Hiệu quả:

+ Đặc biệt hữu dụng đối với các thư viện chương trình, nhất là trong việc cập nhật thư viện(sửa lỗi).

  
- **Cơ chế Overlays**: chỉ giữ trong bộ nhớ những lệnh và DL cần đến tại mọi thời điểm(thường là các Module tải) -> giảm không gian nhớ ltuc dành cho chương trình.
- Cơ chế:
    
    - Cho phép tổ chức ctr thành các đơn vị ctr(module).
    - Module luôn tồn tại trong quá trình thực hiện -> module chương trình chính.
    - Quan hệ độc lập/phụ thuộc chỉ sự có mặt của 1 nhóm module trong bộ nhớ đòi hỏi/không đòi hỏi sự có mặt của một nhóm module khác.
    
    ⇒Các module độc lập không cần thiết phải có mặt đồng thời trong bộ nhớ.
    
- Hiệu quả: cần đến khi Process có dung lượng lớn hơn bộ nhớ được cấp phát cho nó.
  
- **Swapping:**

|   |   |
|---|---|
|![Exported image](Exported%20image%2020240225092707-5.png)|![Exported image](Exported%20image%2020240225092707-6.png)|

  
- **External Fragmentation** – tổng không gian bộ nhớ thực tế đủ đáp ứng yêu cầu, nhưng nó không nằm kề nhau.
- **Internal Fragmentation** – bộ nhớ được phân phối có thể lớn hơn không đáng kể so với bộ nhớ được yêu cầu; sự khác biệt kích thước này là bộ nhớ bên trong một phân vùng, nhưng không được sử dụng.
  
- Giải pháp: Làm giảm external fragmentation bằng cách nén lại

(compaction)

 Di chuyển các nội dung bộ nhớ để đặt tất cả các vùng nhớ tự

do lại với nhau thành một khối lớn.

 Kết khối chỉ có thể tiến hành nếu sự tái định vị là động, và nó

được thực hiện trong execution time.

  
  

  
![Exported image](Exported%20image%2020240225092707-7.png)  
  
  

 **Memory-Management Unit (MMU)**

![Exported image](Exported%20image%2020240225092707-8.png)