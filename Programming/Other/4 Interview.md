### API là gì?
- ***Web API*** : các endpoint được cung cấp thông qua phương thức `HTTP/HTTPS`. Sử dụng bằng cách khi request đến một endpoint cụ thể thì sẽ nhận lại được một response. 
	- Ví dụ : REST API, Graph API
- ***Library API*** : dùng để tương tác giữa các phần mềm trên cùng 1 ứng dụng hoặc môi trường lập trinh. Lập trình viên có thể gọi.
- ***OS API*** : cho phép tương tác với các chức năng của hệ thống như quản lý file, quản lý bộ nhớ, giao tiếp với phần cứng.
- ***DB API*** : dùng để tương tác với cơ sở dữ liệu và thực hiện các thao tác lên dữ liệu.

- API nói chung: 
	- Là các interface để truy cập từ bên ngoài, 
	- Cho phép các hệ thống, chương trình, dịch vụ khác nhau có thể tương tác với nhau. 
	- Chỉ cần gọi và cung cấp các tham số để nhận lại kết quả mà không cần biết chi tiết các hoạt động, xử lý.
### Socket.IO
#### Cơ chế:
- Client gửi request HTTP (handshake) tới để yêu cầu thiết lập kết nối `websocket`.
- Kết nối được thiết lập sau khi request thành công, cho phép trao đổi hai chiều. Lúc này cơ chế `heartbeat` sẽ thực hiện kiểm tra kết nối của cả hai phía.
- Client với server giao tiếp với nhau bằng các sự kiện được định nghĩa từ trước.


