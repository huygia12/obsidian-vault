---
created: 2024-02-25T09:26
updated: 2023-11-16T16:32
---
**Pstree** : Hiển thị đầy đủ của hệ phân cấp các tiến trình cha và con

-p : hiển thị các PID, được sắp xếp tăng dần.

-h : nổi rõ các tiến trình người dùng.

  

**Ps** : xác định tiến trình nào đang thực hiện. Kết hợp với mục đích tìm kiếm:

-ux : hiển thị tất cả các tiến trình thực hiển bởi người dùng.

T : hiển trhij các tiến trình đang chạy bởi thiết bị đầu cuối hiện thời của user.

aux: hiển thị tất cả các process trên hệ thống.

Manpage

  

**Top** : hiển thị thông tin được cập nhật trên các Process tại thời điểm, có thể dùng để thay đổi priority của Process.

h : hiển thị danh sách các lệnh hỗ trợ

  

**Kill SIGNAL process_PID** : dừng Process, tiến hiệu mặc định dừng Process là SIGTERM.

![Exported image](Exported%20image%2020240225092649-0.png)  

**Killall SIGNAL process_Name** :

  

**Nice -<NI> process**: để thiết lập mức độ ưu tiên của một Process. Các Process bắt đầu với giá trị NI là 0, chỉ có người quản trị hệ thống có thể thiết lập giá trị âm cho các giá trị NI.

  

**Renice <+/-NI> -p <PID>**: thay đổi mức độ ưu tiên của một Process.

-u : ảnh hưởng đến tất cả các Process thực hiện bởi người dùng.

  

**Ctrl Z** : thực hiện ngắt chươntg trình tạm thời trong nền trước.

  

Fg : chạy chươn trình trong nền trước của Shell.

  

Bg: chạy chươn trình trong nền sau của Shell;