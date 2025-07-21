DeadLock: là hiện tượng một Process chiếm hữu tài nguyên lâu dài làm cho các Process có như cầu sd tài nguyên này luôn ở trạng thái Waiting.

-> Process DeadLock là Process không bao giờ xảy ra.

  
![Exported image](Exported%20image%2020240225092717-0.png)  

  
2. **Mô tả hệ thống**:
3. Các loại tài nguyên ký hiệu: R1, R2, …. Rn.
4. Mỗi loại tài nguyên Ri có Wi cá thể(Instance). VD: Tài nguyên CPU có 4 cá thể(4CPU),….
5. Mỗi Process sd tài nguyên theo các bước:
    
    - Yêu cầu tài nguyên(Request): nếu tài nguyên đã bận thì Process yêu cầu phải đợi cho đến khi nhận được tài nguyên.
    - Sử dụng tài nguyên(Use).
    - Giải phóng tài nguyên(Release).
      
    
6. **Biểu đồ phân phố tài nguyên - RAG**:
![Exported image](Exported%20image%2020240225092717-1.png)8. Đồ thị không chu trình thì không có Process nào bị DeadLock; Đồ thị có chu trình thì có thể có Process bị DeadLock(Nếu có 1 cá thể thì chắc chắn xảy ra DeadLock, còn nếu có 1 vài cá thể thì DeadLock có thể xảy ra).
9. **Ngăn ngừa DeadLock**:
![Exported image](Exported%20image%2020240225092717-2.png) ![Exported image](Exported%20image%2020240225092717-3.png)  
13. **Thoát khỏi DeadLock**:
![Exported image](Exported%20image%2020240225092717-4.png)  
16. **Giải thuật chủ nhà băng**: được sử dụng trong hệ thống nhà băng để đảm bảo không bao giờ phân phối quá số tiền khả dụng của nó để luôn thỏa mãn mọi yêu cầu từ khách hàng.
17. Khi 1 Process mới đi vào hệ thống: Phải khai báo n(SL tối đa các thể của mỗi loại tài nguyên mà nó có thể cần đến) với n có thể lớn hơn tổng tài nguyên trong hệ thống.
18. Khi 1 Process yêu cầu tài nguyên, hệ thống phải xác định liệu sự phân phối có giữ hệ thống trong trạng thái an toàn không: Nếu có thì phân phối tài nguyên; Không thì đợi đến khi các Process khác giải phóng tài nguyên.
  
20. CTDL:
  
22. Kiểm tra chuỗi an toàn: Nếu tìm mỗi chuỗi là an toàn thì hệ thống là an toàn, trái lại trạng thái là không an toàn.
![Exported image](Exported%20image%2020240225092717-5.png)  
25. Giải quyết yêu cầu tài nguyên cho Process Pi:
![Exported image](Exported%20image%2020240225092717-6.png)  
28. **Phát hiện DeadLock**:
29. Mỗi loại tài nguyên có 1 cá thể: xác định deadlock sd một biến thể của, bằng cách bỏ đi các nút của loại tài nguyên và bỏ đi các cạnh thích hợp-> Wait-for-Graph.
    
    - Các nút là các Process: n.
    - Pi -> Pj nếu Pi đang đợi Pj.

+ Định kỳ sd giải thuật tìm kiếm chu trình trong đồ thị(thuật toán sắp xếp Topo), đòi hỏi n2 phép toán

31. Mỗi loại tài nguyên có nhiều cá thể:

+ Available: vecto đọ dài m là xd số tài nguyên khả dụng mỗi loại.

+ Allocation: ma trận nxm xd số tài nguyên của mỗi loại hiện đang được phân phối cho từng Process.

+ Request: ma trận nxm, nếu Request[i,j]=k thì Process Pi đang yêu cầu k cá thể nữa của loại tài nguyên Rj.

  
36. Giải thuật phát hiện DeadLock:
37. Nhận xét:

+ Thời điểm và mức thường xuyên cần đến giải thuật phụ thuộc vào DeadLock có khả năng thường xuyên xảy ra thế nào và có bao nhiêu Process bị tác động.

+ Càng ít sử dụng giải thuật phát hiện DeadLock càng có khả năng nhiều chu trình tồn tại nên ta không thể tìm được những Process nào gây ra DeadLock.

  
41. **Phục hồi từ DeadLock**:
42. Dừng Process:
![Exported image](Exported%20image%2020240225092717-7.png)  
45. Ưu tiên trước tài nguyên:
![Exported image](Exported%20image%2020240225092717-8.png)  
48. Phương pháp kết hợp xử lý DeadLock:
![Exported image](Exported%20image%2020240225092717-9.png)  

  
![Exported image](Exported%20image%2020240225092717-10.png)  
  
  
![Exported image](Exported%20image%2020240225092717-11.png)  
  
  

+ Nếu có chu trình -> có thể có DeadLock.

![Exported image](Exported%20image%2020240225092717-12.png)  
  
![Exported image](Exported%20image%2020240225092717-13.png)