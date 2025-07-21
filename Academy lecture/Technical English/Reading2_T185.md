---
created: 2024-03-20T21:53
updated: 2024-03-22T17:21
tags:
  - English
  - Technical
---
# Dịch thuật :


 Mặc dù phát triển các ứng dụng di động về cơ bản không khác biệt so với việc phát triển web/máy tính bàn truyền thống về mặt quá trình hay kiến trúc, nhưng nó vẫn có một số điều cần cân nhắc. Cùng xem một số điều cần lưu ý thường thấy, sau đó chúng ta sẽ xem xét một số cân nhắc cụ thể về nền tảng.
### Một số điểm cần xem xét thường thấy :
*Đa nhiệm*
- Có hai thách thức cần xem xét về vấn đề đa nhiệm (có nhiều ứng dụng chạy cùng lúc) trên một thiết bị di động. Đầu tiên, với kích thước màn hình giới hạn, điều đó là rất khó để hiển thị đa ứng dụng cùng lúc. Vì thế, trên các thiết bị di động chỉ có một ứng dụng có thể chạy trong lớp nền trên tại một thời điểm. Thứ hai, việc có nhiều ứng dụng mở và hoạt động có thể tốn nhiều năng lượng pin. 
- Mỗi nền tảng triển khai đa nhiệm khác nhau, chúng ta sẽ xem qua một chút về điều này.

*Loại hình dạng*
- Các thiết bị di động nói chung thường chia làm hai loại, các máy điện thoại và các máy tablet, một số thì lai tạp giữa cả hai. Việc phát triển cho những loại này nói chung là giống nhau, tuy nhiên thiết kế những ứng dụng cho chúng có thể rất khác. Những chiếc điện thoại thì có không gian hiển thị rất hạn chế, và các tablet mặc dù lớn hơn, vẫn là thiết bị di động với rất ít không gian hiển thị so với hầu hết các máy tính xách tay. Vì thế, các thiết bị điều khiển UI trên nền tảng di động đã được thiết kế đặc biệt để hoạt động hiệu quả trên các loại hình dạng nhỏ hơn.
### Phân hóa theo hệ điều hành và thiết bị
Điều quan trọng là phải tính đến các thiết bị khác nhau trong toàn bộ vòng đời phát triển phần mềm : 
	1. Khái niệm hóa và lên kế hoạch - bởi vì các thiết bị khác nhau có thể có các tính năng thiết bị và phần cứng khác nhau, bạn nên giữ trong đầu rằng một ứng dụng mà dựa trên những tính năng nhất định sẽ không hoạt đông chính xác trên những thiết bị cụ thể. Lấy ví dụ, không phải các thiết bị đều có cameras, vậy nên nếu bạn xây dựng một ứng dụng truyền tin bằng hình ảnh, một số thiết bị sẽ có thể phát video, nhưng một số thì không.
	2. Thiết kế - Khi thiết kế đến trải nghiệm người dùng của ứng dụng (UI), những cái tỉ lệ và kích thước màn hình khác nhau nên cần được suy xét. Thêm nữa, khi thiết kế giao diện người dùng của một ứng dụng (UI), những độ phân giải màn hình khác nhau cần được cân nhắc. 
	3. Phát triển - Khi sử dụng một tính năng từ mã lệnh, sự hiện diện của tính năng đó cần phải được kiểm tra đầu tiên. Lấy ví dụ, trước khi sử dụng tính năng trên thiết bị, như là camera, phải luôn truy tìm sự hiện diện của tính năng đó trên hệ điều hành trước. Sau đó, khi bắt đầu tính năng/thiết bị, đảm bảo yêu cầu để được hỗ trợ từ hệ điều hành ngay lúc này về thiết bị đó và sau đó sử dụng những cài đặt cấu hình này.
	4. Kiểm thử - Việc sớm kiểm tra ứng dụng của bạn là rất quan trọng và thường được triển khai trên các thiết bị thật. Kể cả khi các thiết bị có cùng thông số phần cứng có thể có cách hoạt động khác nhau.

*Những nguồn tài nguyên giới hạn*
- Các thiết bị di động ngày càng mạnh mẽ hơn, nhưng chúng vẫn là những thiết bị di động mà có khả năng giới hạn so với máy tính bàn hay những chiếc máy tính xách tay. Lấy ví dụ, những người phát triển máy tính bàn thường không lo lắng về vấn đề lưu trữ bộ nhớ, trong khi trên các thiết bị di động bạn có thể tiêu thụ toàn bộ bộ nhớ khả dụng nhanh chóng chỉ bằng cách tải lên một số hình ảnh chất lượng cao.
- Thêm vào đó, những ứng dụng sử dụng nhiều bộ xử lý như là các trò chơi hay nhận diện văn bản có thể thực sự có thể là gánh nặng cho CPU của thiết bị di động và ảnh hướng xấu đến hoạt động của thiết bị.
- Vì những điều cần cân nhắc như trên, điều quan trọng là cần viết mã một cách thông minh để triển khai sớm và thường xuyên lên các thiết bị thật để làm xác thực sự linh hoạt.

*Những điểm cần xem xét về iOS*
- Đa nhiệm
	Đa nhiệm được kiểm soát chặt chẽ trong iOS, và có một số điều luật và hành vi mà ứng dụng của bạn phải tuân thủ theo khi một ứng dụng khác chạy trên lớp nền trên, không thì ứng dụng của bạn sẽ bị dừng bởi iOS.
- Những tài nguyên cụ thể trên thiết bị
	Trong một dạng cụ thể, phần cứng có thể khác nhau rất nhiều trên các mẫu máy khác nhau. Lấy ví dụ, một số thiết bị có một camera phía sau, một số lại còn có một camera phía trước, và một số thì không.
	Một vài các thiết bị cũ hơn (iPhone 3G và cũ hơn) thậm chí còn không cho phép đa nhiệm. Vì những sự khác nhau này giữa các mẫu thiết bị, điều quan trọng là phải kiểm tra sự hiện diện của một tính năng trước khi có ý định sử dụng nó.
- Những ràng buộc cụ thể của hệ điều hành
	Để đảm bảo các ứng dụng linh hoạt và an toàn, iOS thực thi một số điều luật mà các ứng dụng phải ràng buộc theo. Bên cạnh những điều luật liên quan tới đa nhiệm, có một số những sự kiện mà ứng dụng của bạn phải quay lại trong một khoảng thời gian nhất định, nếu không nó sẽ bị dừng lại bởi iOS.
	Cũng phải lưu ý, những ứng dụng hoạt động trên Sandbox, một môi trường mà thực thi các ràng buộc bảo mật mà giới hạn những gì ứng dụng của bạn có thể truy cập. Lấy ví dụ, một ứng dụng có thể đọc và ghi vào thư mục của nó, nhưng nếu nó cố để ghi vào một thư mục của ứng dụng khác, nó sẽ bị dừng.

*Những điểm cần xem xét về Android*
- Đa nhiệm 
	Vấn đề đa nhiệm trên Android có hai phần; đầu tiên là vòng đời hoạt động. Mỗi màn hình trên một ứng dụng Android được đại diện bởi một Hoạt động, và có một bộ các sự kiện cụ thể sẽ xảy đến khi một ứng dụng được đặt trong lớp nền dưới hoặc chuyển sang lớp nền trên. Các ứng dụng phải tuân thủ theo vòng đời để tạo ra các ứng dụng tốt, có khả năng linh hoạt. Để rõ hơn, hãy tìm hiểu về hướng dẫn Vòng Đời Hoạt Động.
	Thành phần thứ hai của đa nhiệm là chức năng của các dịch vụ. Các dịch vụ là các tiến trình dài tồn tại độc lập của một ứng dụng và được sử dụng để thực thi các tiến trình khác khi ứng dụng ở trên lớp nền dưới. Để rõ hơn hãy tìm hiểu về hướng dẫn Tạo Các Dịch Vụ.
-  Các thiết bị và các hình dạng
	Không như iOS, chỉ có một vài thiết bị nhỏ, hay thậm chí là điện thoại Windows, chỉ chạy trên các thiết bị được phê duyệt đáp ứng một bộ các nhu cầu tối thiểu, Google không áp đặt bất kì giới hạn nào về thiết bị nào có thể hoạt động trên hệ điều hành Android. Mô hình mở này dẫn đến một môi trường sản phẩm có vô số những thiết bị khác nhau với phần cứng, tỉ lệ và độ phân giải màn hình, các tính năng và các khả năng cũng khác nhau.
	Bởi vì sự phân hóa quá mức của các thiết bị Android, một số người chọn 5-6 thiết bị phổ biến nhất để thiết kế và kiểm thử, và ưu tiên những thiết bị này.
- Những cân nhắc về bảo mật :
	Các ứng dụng trên hệ điều hành Android đều hoạt động dưới một định danh riêng biệt với các quyền hạn chế. Mặc định, các ứng dụng có rất ít việc có thể . Ví dụ, nếu không có các quyền đặc biệt, một ứng dụng không thể gửi một tin nhắn văn bản, xác định trạng thái điện thoại, hoặc thậm chí truy cập đến Internet! Để có thể truy cập những tính năng này, các ứng dụng cần phải chỉ rõ trong tập tin kê khai của ứng dụng đó những quyền mà chúng muốn, và khi chúng đã được cài đặt; hệ điều hành đọc những cái quyền này, thông báo cho người dùng rằng ứng dụng đang yêu cầu những quyền này, và sau đó cho phép người dùng tiếp tục hoặc hủy bỏ qua trình cài đặt. Đây là một bước quan trọng trong mô hình phân phối của Android, vì là mô hình cửa hàng ứng dụng mở, như là việc ứng dụng không được kiểm định như cách mà iOS làm. Về danh sách các quyền của ứng dụng, xem bài viết Tham Khảo Những Quyền Kê Khai trong Tài Liệu Android.

*Những điểm cần xem xét về điện thoại Windows*
- Đa nhiệm :
	Đa nhiệm trên máy điện thoại Windows gồm hai phần : vòng đời cho các trang và các ứng dụng, và các tiến trình ở lớp nền dưới. Mỗi màn hình trong một ứng dụng là một biểu hiện của lớp Trang, nó có các sự kiện gắn liền với việc được kích hoạt hay không kích hoạt (với các luật lệ đặc biệt để xử lý những trạng thái chưa kích hoạt, hoặc bị "xuống mồ"). Để biết thêm thông tin hãy xem Tổng Quan Về Mô Hình Thực Thi dành cho tài liệu điện thoại Windows.
	Phần thứ hai là cung cấp tác nhân nền để thực hiện các tác vụ cả khi ứng dụng không chạy trong lớp nền trên. Để biết thêm thông tin cách lên lịch các tách vụ định kì hoặc tạo các tác vụ tiêu tốn tài nguyên trong lớp nền dưới có thể được tìm thấy trong Tổng Quan Các Tác Nhân Nền. 
- Các khả năng của thiết bị :
	Mặc dù phần cứng điện thoại Windows khá đồng nhất bởi vì những chỉ dẫn nghiêm ngặt được đưa ra bởi Microsoft, vẫn có những thành phần là tùy chọn và vì vậy yêu cầu cần xem xét đặc biệt khi lập trình. Các tùy chọn chức năng phần cứng bao gồm camera, la bàn, con quay hồi chuyển. Ngoài ra còn có một loại bộ nhớ thấp đặc biệt (256MB) cần được xem xét đặc biệt, hoặc những người phát triển có thể từ chối hỗ trợ bộ nhớ thấp.
- Cơ sở dữ liệu :
	Cả iOS và Android đều có cơ sở dữ liệu SQLite cho phép lưu trữ dữ liệu tinh vi có thể hoạt động đa nền tảng. Điện thoại Windows 7 không bao gồm một cơ sở dữ liệu, trong khi Điện thoại Windows 7.1 và 8 bao gồm 1 công cụ cơ sở dữ liệu có thể được truy vấn với LINQ hoặc SQL và không hỗ trợ các truy vấn Transact-SQL. Có sẵn một cổng nguồn mở của SQLite có thể được thêm vào các ứng dụng điện thoại Windows để cung cấp hộ trợ Transact-SQL và tương thích với đa nền tảng. 
- Những điều cần cân nhắc về bảo mật 
	Những ứng dụng điện thoại Windows hoạt động với một bộ các quyền nghiêm ngặt tách biệt chúng khỏi những thứ khác và giới hạn những quá trình chúng có thể thực hiện. Truy cập mạng phải được thực hiện thông qua các API cụ thể và việc giao tiếp giữa các ứng dụng có thể được hoàn thành thông qua các cơ chế điều khiển. Truy cập đến hệ thống tập tin cũng bị hạn chế; Bộ nhớ API biệt lập cung cấp lưu trữ theo cặp khóa-giá trị và khả năng tạo các tập tin và các thư mục theo cách được kiểm (tham khảo Tổng quan bộ nhớ biệt lập để biết thêm thông tin).
	Quyền truy cập của ứng dụng vào các tính năng phần cứng và hệ điều hành được kiểm soát bởi các khả năng được liệt kê trong tệp kê khai của ứng dụng đó (tương tự như Android). Tệp kê khai phải khai báo các tính năng mà ứng dụng yêu cầu để người dùng có thể xem và đồng ý với các quyền đó cũng như để hệ điều hành cho phép truy cập vào API. Các ứng dụng phải yêu cầu quyền truy cập vào các tính năng như dữ liệu danh bạ hoặc cuộc hẹn, máy ảnh, vị trí, thư viện phương tiện, v.v. Xem tài liệu về Tệp kê khai ứng dụng của Microsoft để biết thêm thông tin


---


# Tóm tắt :
Phát triển các ứng dụng di dộng về cơ bản không khác so với phát triển ứng dụng web/máy tính bàn nhưng vẫn có một số điều cần phải xem xét. Đầu tiên là vấn đề về đa nhiệm như hiển thị đa ứng dụng với kích thước màn hình bị giới hạn cũn như vấn đề về pin khi chạy nhiều ứng dụng. Thứ hai là vấn đề về loại hình dạng sẽ dẫn tới việc ứng dụng cần được thiết kế đặc biệt để hoạt động hiệu quả trên từng loại. Cần phải tính đến các loại thiết bị trong suốt vòng đời phát triển: khái niệm niệm hóa và lên kế hoạch, thiết kế, phát triển và kiểm thử. Các thiết bị di động mặc dù ngày càng mạnh hơn nhưng khả năng vẫn còn bị giới hạn hơn so với máy tính. Đối với hệ điều hành iOS, đa nhiệm được kiểm soát nghiêm ngặt, vì phần cứng khác nhau nên phải kiểm tra trước khi sử dụng một tính năng nào đó. Bên cạnh đó iOS cũng đưa ra các điều khoản riêng mà các ứng dụng phải tuân theo, giới hạn quyền mà ứng dụng có thể thực thi. Còn đối với Android, để thực hiện được đa nhiệm thì ứng dụng phải tuân thủ theo vòng đời hoạt động, thực thi các tiến trình khác trong nền dưới bằng chức năng của các dịch vụ. Thiết bị android không chịu bát kì giới hạn nào về hệ điều hành, phần cứng, độ phân giải màn hình,... Các ứng dụng trên hệ điều hành này cũng phải khai báo rõ những quyền chúng muốn và sau đó được khi cài đặt sẽ thông báo cho người dùng biết để tiếp tục cho phép hay không. Cuối cùng là trên điện thoại Windows, việc đa nhiệm thể hiện trong việc các tiến trình chạy trong lớp nền dưới bởi các tác nhân nền trong khi ứng dụng hoặc các trang thực hiện ở lớp trên. Phần cứng điện thoại Windows tương đối đồng nhất giữa các loại mẫu mã nhưng vẫn có các chức năng là tùy chọn và cần phải cân nhắc. Giống như iOS và Android, điện thoại Window cũng hỗ trợ các công cụ quản lý và truy vấn cơ sở dữ liệu. Các ứng dụng windows bị giới hạn những quyền và khả năng chúng có thể làm; truy cập mạng phải được thực hiện thông qua các API cụ thể và giao tiếp giữa các ứng dụng có thể được hoàn thành thông qua các cơ chế điều khiển. Quyền truy cập của ứng dụng vào các tính năng phần cứng và hệ điều hành được kiểm soát bởi những gì đã khai báo trong tệp kê khai của ứng dụng đó (tương tự như Android).








