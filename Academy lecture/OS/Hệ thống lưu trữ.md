1. **Disk-Structure(Cấu trúc ổ c****ứng****)**:
2. Đĩa được đánh địac chỉ là mảng 1 chiều của các khối logic(là đơn vị nhỏ nhất trong chuyển DL).
3. Mảng 1 chiều của các khối logic được ánh xạ vào các Sector của đĩa một cách tuần tự.
    
    + Sector là đơn vị lưu trữ nhỏ nhất.
    
    + Sector 0 là Sector đầu tiên của Track đầu tiên trên Cylinder ngoài cùng.
    
    + Việc ánh xạ tiếp tực theo thứ tự qua Track đó, rồi đến các Track còn lại trong Cylinder đó, rồi đến các Cylinder còn lại từ ngoài vào trong.
    
    - Track: một vòng tròn quanh tâm đĩa.
    - Sector: đơn vị nhỏ nhất để lưu trữ được phân vùng trên mỗi Track.
    - Cylinder: là tập hợp Track trên các mặt đĩa mà có cùng vtri(tạo thành hình trụ).
    - Dung lượng ổ đĩa = 2*(SL đĩa)*Số-Track*Số-Sector-trên-1Track
      
    
4. Thời gian đọc vùng trên ổ đĩa cần quan tâm 2 loại thời gian:

+ Trong hệ thống I/O đĩa thời gian để đầu đọc đến đúng khối cần thiết trên một Track là Latency-Time = Thời gian định vị(Seek-Time)+Trễ quay(Rotational Latency).

+ Thời gian đầu đọc đến đúng Track trên ổ đĩa gọi là Seek-Time.

  
8. **Disk-Scheduling**:
![Exported image](Exported%20image%2020240225092709-0.png) ![Exported image](Exported%20image%2020240225092709-1.png)

![Exported image](Exported%20image%2020240225092709-2.png)

_Đĩa cứng HDD_

  
  
  

1. **FCFS(First Come, First Serverd):**
![Exported image](Exported%20image%2020240225092709-3.png)  
4. **SSTF(Shortest Seek Time First):**
![Exported image](Exported%20image%2020240225092709-4.png)  
7. **SCAN:**
8. **C-SCAN(Circular SCAN):**
9. **LOOK và C-LOOK:**
10. **Lựa chọng một giải thuật lập lịch đĩa:**

  
  
  

  
2. **RAID:**