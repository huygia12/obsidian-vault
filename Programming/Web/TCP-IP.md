---
tags:
  - Web
created: 2024-02-26T00:52
updated: 2024-02-26T11:41
---
# Concept :
- TCP/IP là giao thức điều khiển truyền nhận/ giao thức liên mạng. Đây là 1 bộ các giao thức truyền thông được sử dụng để kết nối các thiết bị với nhau trên Internet (để các thiết bị có thể giao tiếp được với nhau thì phải hiểu cùng 1 ngôn ngữ).
- Hoạt động như 1 lớp trừu tượng giữa các ứng dụng internet và hạ tầng router/switch.
- Họat động độc lập với HDH.
- TCP và IP là hai giao thức chính bên cạnh những giao thức khác trong bộ.

# Work flow :
- TCP hoạt động với giao thức Internet (IP) để chỉ định các data được trao đổi trực truyến.
	- IP chịu trách nhiệm định tuyến gói tin giữa các mạng, thông qua 1 hay nhiều trạm chuyển tiếp.
	- TCP đảm bảo các byte được truyền theo thứ tự mà chứng gửi đảm bảo truyền tải một cách tin cậy và có thứ tự. TCP giúp kiểm tra các gói xem có lỗi không sau đó gửi theo yêu cầu truyền lại nếu có lỗi.

> Từ đó xác định cách data được chia thành các packet, xác định địa chỉ, định tuyến và nhận gữ liệu.
> Nó có khả năng khôi phục tự động khi gặp sự cố trong quá trình truyền dữ liệu.

# TCP/IP layers :
![[Pasted image 20240226095112.png]]
- Physical :
	- Đây là sự kết hợp giữa tầng Physical và DataLInk của mô hình OSI.
	- Tầng này chịu trách nhiệm truyền data giữa hai thiết bị trong cùng 1 mạng.
	- Tại đây, gói dữ liệu được đóng vào khung gọi là Frame.
	- Frame được định tuyến đến đích đã được chỉ định ban đầu.

- Internet :
	- Tương đương với tầng Network của mô hình OSI, chịu trách nhiệm truyền tải data 1 cách logic trong mạng.
	- Data được đóng gói thành Packets.
	- Packages được chèn thêm thành phần Header chứa thông tin của tầng và tiếp tục được chuyển đến tầng tiếp theo.
	- Các giao thức chính trong tầng là IP, ICMP[^1] và ARP[^2]

- Transport :
	- Xử lý vấn đề giao tiếp giữa các máy chủ trong cùng 1 mạng hoặc khác mạng được kết nối với nhau thông qua Router.
	- Data được đóng gói thành Segments và lại chèn thêm thành phần Header chứa thông tin của tầng và tiếp tục được chuyển đến tầng tiếp theo.
	- Hai giao thức chính là TCP[^3] và UDP[^4]

- Aplication :  ^b34392
	- Đảm nhận vai trò giao tiếp dữ liệu giữa 2 máy khác nhau thông qua các dịch vụ mạng khác nhau như duyệt web, chat, emial hoặc một số giao thức trao đổi dữ liệu SMTP, SSH, FTP, ...
	- Data được định dạng theo kiểu Byte nối Byte, cùng với đó là các thông tin định tuyến giúp xác định đườn đi đúng của 1 gói tin.

![[Pasted image 20240226103622.png]]

# 3 way handshake : 
-  Theo tiến trình 3 bước (3 way handshake).
	![[Pasted image 20240226005604.png]]
	- Client gửi cho Server một gói SYN đẻ yêu cầu kết nối từ port của Client đến port đích của Server.
	- Server phản hồi bằng gói SYN/ACK, xác nhận việc nhận được yêu cầu kết nối.
	- Server nhận gói SYN/ACK và trả lời bằng gói ACK  của chính Server.
> Dữ liệu sau đó được chia nhỏ thành các Segment (phân đoạn) được đóng gói thành 1 Package và được gửi đến đích.

# Cấu trúc của TCP Header : 
![[Pasted image 20240226010422.png]]

[^1]: ICMP : Internet COntrol Message Protocol.
[^2]: IGMP : Internet Group Mesage Protocol.
[^3]: TCP : Chia nhỏ các gói tin ở tầng trên thành các gói tin có kích thước thích hợp cho tần mạng bên dưới, baaos nhận gói tin, đặt hạn chế thời gian timeout để đảm bảo bên nhận được các gói tin đã gửi đi.
[^4]: UDP : User Datagram Protocol, gửi liệu từ trạm này tới trạm kia mà không đảm bảo các gói tin đến được tới đích.