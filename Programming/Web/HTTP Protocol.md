---
tags:
  - Web
created: 2024-02-24T21:58
updated: 2024-04-23T15:48
---
# Concept :
- Là giao thức hoạt động trên cơ sở của TCP/IP. Sau khi đã nhận được địa chỉ của máy chủ web được trả về từ máy chủ [[DNS]] HTTP sử dụng TCP để thiết lập kết nối và truyền tải dữ liệu giữa client và server. Khi Client gửi HTTP Request đến 1 Server, một kết nối TCP sẽ được thiết lập giữa hai máy, sau đó data sẽ được truyền qua kết nối này. 
- HTTP sử dụng cấp độ truyền tải dữ liệu cao hơn :
	- HTTP hoạt động ở tẩng Application trong mô hình [[TCP-IP]]. Trong khi TCP là 1 phần của tầng Transport.
	- HTTP sử dụng TCP để truyền tải data. HTTP xác định các thông điệp như Request và Reponse được đóng gói và gửi qua mạng, trong khi TCP xác định cách data được chia thành các package.
- Về cơ bản, khi nhập 1 URL vào trình duyệt của mình, 1 HTTP Request được gửi đến máy chủ lưu trữ ứng dụng để tìm và truyền tải trang web được yêu cầu thông qua TCP.

# HTTP Request :
- Là tập hợp thông tin từi các máy Client đến Server, yêu cầu được tìm kiếm hoặc xử lý và phản hồi kết quả lại Client.
- HTTPRequest có thể là file XML hoặc Json (cả hai phía đều hiểu được).

##### HTTP request structure：
- Bất cứ HTTPRequest nào cũng có cấu trúc cụ thể gồm 3 thành phần chính là Request-line, Request-header, Body-Request.

	>![[HTTPHeader.png]]

* Request-Line : bao gồm 3 yếu tố :
	* Phương thức HTTP được sử dụng.
	* URL được yêu cầu, thông thường là 1 đường dẫn tới 1 tài nguyên và 1 chuỗi các tham số mà Client gửi tới Server.
	* Phiên bản của HTTP Protocol.

- Request-Header : Giúp các yêu cầu từ client có thể chuyển đến Server. Các thông số bên trong là Header-Parameters.
	- Accept : định dạng dữ liệu được hỗ trợ.
	- User Agent : giúp máy chủ xác định được nhà cung cấp, ứng dựng, hdh, phiên bản.
	- Connection : cho phép hệ thống tiếp tục hoặc dừng kết nối sau khi máy chủ xử lý xong các Request.
	- Cache-Control : thực hiện chính sách bộ nhớ đệm mà trình duyệt phụ trách.
	- Accept-Language : các ngôn ngữ mà Client có thể hiểu được.

- Request-Body : có chức năng giúp các Client gửi được request bổ sung tới server. Có thể sử dụng tạo mới, cập nhật data mà Header-parameters không truyền đi được, sử dụng ba phương thức chính là Post, Patch và Put.

##### HTTP Request methods :

>![[Pasted image 20240224234812.png]]

- ***Get*** là phương thức được máy client sử dụng để gửi dữ liệu tới server thông qua URL(trên thanh địa chỉ của Browser).
	- Không cần phải có Request body
	- Độ dài các giá trị được giới hạn trong 255 kí tự.
	- Chỉ các data kiểu String mới được hỗ trợ.
	- Thông tin request data được lưu vào bộ nhớ cache.
	- Không được dùng phương thức GET khi truy vấn thông tin nhạy cảm tới Server.
	- Lịch sử trình duyệt lưu trữ các tham số được truyền vào (có thể xem lại).

- ***Post***  sử dụng để gửi data đến Server. User thêm data mới hoặc cập nhật data vào DataBase.
	- Các data bổ sung sẽ không xuất hiện trong URL của trình duyệt.
	- Có thể dùng để truy vấn các thông tin nhạy cảm, quan trọng.
	- Post không giới hạn độ dài ký tự, hỗ trợ nhiều kiểu data khác nhau (String, integer, binary).

- ***Put*** là phương thức có chức năng rất giống Post. CHủ yếu được sử dụng cập nhật data cũ của đối tượng.

- ***Head*** kiểm tra hoạt dộng của API có ổn định hay không.
	- Được sử dụng phở biến trước khi tải file.
	- Phương thức không chứa request body.

- ***Delete*** là phương thức dùng để xóa các data tìm kiếm từ Server về tài nguyên thông URL.
	- Phương thức không chứa request body -> thời gian xử lý nhanh.
	
	>![[Pasted image 20240226003409.png]]

- ***Patch***  thay vì cập nhật toàn bộ data đã có trong database như Put thì Patch chỉ cập nhật 1 phần data của đối tượng.

- ***Option***, ***Connect***, ***Trace***,...
# HTTP Response :
##### HTTP Response  structure:
- Response Line : bao gồm 3 phần được phân tách bởi dấu cách. 
	- Phiên bản của giao thức HTTP.
	- Result code.
	- Chuỗi kí tự mô tả trạng thái của phản hồi thường là lời giải thích cho mã kết quả truy vấn (có thể bị bỏ qua).

- Body :
	- Content Type : định dạng dữ liệu của phần thân.
	- Content length : độ dài của thân phản hồi (tính bằng byte).
	- Set-cookie : Thiết lập giá trị cookie mới cho client. Giá trị này lại dược gửi lại cho server trong truy vấn kế tiếp.
	- Các thông tin còn lại thể hiện cách thức mã hóa dữ liệu hoặc điều phối dữ liệu của Server.

##### Status code range : được nhóm theo chữ số đầu tiên
- 1xx : Thông tin response.
- 2xx : Request đã thành công.
- 3xx : Máy khách được chuyển hướng đến 1 tài nguyên khác.
- 4xx : Request có chứa 1 số lỗi.
- 5xx : Server gặp lỗi khi thực hiện request.

##### Một số Status code phổ biến :
- 200 : Truy vấn thành công.
- 404 : Request đã được nhận nhưng không thể tìm thấy tài nguyên. 
- 401 : Client phải thực hiện authentication trước tiên.
- 500 : Mang ý nghĩa răng một số lỗi bên trong HTTP Server ngăn chặn nó hoàn thành Request.
- 503 : Mang ý nghĩa răng HTTP Server tạm thời bị quá tải (Overloaded) không thể handle Request.
- 202: Accepted, request được thực hiện, nhưng quá trình xử lý chưa hoàn tất.

# RFC 3986
- Tiêu chuẩn định nghĩa về `URI`, được sử dụng trong hầu hết các hệ thống giao tiếp bằng http
	- Các ký tự được cho phép trong query parameters:
		- Chữ cái từ a-z, A-Z
		- Số 0-9
		- Ký tự đặc biệt an toàn `-, _, ., ~`
	- Các ký tự khác đều phải được mã hóa: chuyển sang dạng HEX và thêm % vào trước.

---
# Reference :
[ About 204 & 205 response codes]([https://web.archive.org/web/20230918193536/https://benramsey.com/blog/2008/05/http-status-204-no-content-and-205-reset-content/ )






