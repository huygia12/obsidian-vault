1. **Dual-Mode**: các tài nguyên hệ thống chia sẻ (**Sharing System resources**) yêu cầu HDH đảm bảo rằng một chương trình bị lỗi không thể gây cho các chương trình khác thực hiện sai theo.
2. HDH phải cung cấp phần cứng để phân biệt giữa ít nhất 2 chế độ thực hiện : **UserMode** và **MonitorMode**(tư cách HDH):
    
    - Thêm 1 bit (Mode bit) được đưa vào phần cứng máy tính để chỉ rõ chế độ hiện tại Monitor(0) hoặc User(1).
    - Trong đó Monitor được toàn quyền truy xuất tài nguyên hệ thống, có quyền hạn chế của user bình thường.
3. Khi chương trình người dùng đang được thực thi thì một ngắt hoặc lỗi xuất hiện(là khi chương trình muốn thao tác với nhân hoặc phần cứng…), phần cứng chuyển sang monitor mode:
4. **I/O protection**: tránh việc user thực hiện các vào-ra không hợp lệ phá vỡ hệ thống thì các lệnh vào-ra đều phải là đặc quyền.
5. User không thể thực hiện trực tiếp vào-ra mà phải thông qua các lời gọi hệ thống(**system call**).
6. **System call**: là lời gọi sử dụng các dịch vụ HDH cung cấp dùng để giao tiếp giữa HDH và Process, thường được viết bằng ngôn ngữ assembly.
7. **Memmory Protection**:
8. Sử dụng hai thanh ghi base&limit (tùy thuộc vào CPU).
9. **Giới hạn vùng nhớ truy cập** căn cứ vào giá trị thanh ghi base&limit: tránh vùng nhớ dành cho ngắt bị thay đổi bởi chương trình người dùng.
10. **CPU Protection**:
11. Timer-ngắt máy tính trong khoảng thời gian được định sẵn để HDH duy trì sự điều khiển, tránh chương trình người dùng bị kẹt trong 1 vòng lặp vô hạn: timer giảm sau 1 khoảng thời gian xác định khi đến giá trị 0, một ngắt xuất hiện.

- Chương trình người dùng _gọi đến lời gọi hệ thống_ (**system call**) -> _đổi bit usermode =0(xin phép hdh)_-> nếu việc **đổi hoàn tất** thì _trả lại giá trị usermode = 1_ rồi chạy tiếp chương trình người dùng.

![Exported image](Exported%20image%2020240225092726-0.png)

- Gây ngắt mềm -> HDH chuyển điều khiển cho các chương trình phục vụ ngắt, usermode = 0 -> HDH kiểm tra các đối số, thực hiện yêu cầu, chuyển điều khiển đến lệnh tiếp theo, chuyển lại usermode = 1.

  
![Exported image](Exported%20image%2020240225092726-1.png)