---
created: 2024-02-25T11:30
updated: 2024-01-01T00:44
---
- **Java IO****: java.io.File**

  
![Exported image](Exported%20image%2020240225113003-0.png) ![Exported image](Exported%20image%2020240225113003-1.png)  

- Một số phương thức thường dùng:
  
- Sử dụng System.getproperty("user.dir") để trả về chuỗi là đường dẫn tuyệt đối đến folder hiện tại đang chạy chương trình
- Sử dụng File.separator để trả về kí tự ngăn cách theo hệ điều hành hiện tại(\ hoặc /)
- Sử dụng ten_file.getAbsolutePath để lấy đường dẫn tuyệt đối đến file chỉ định
- Liệt kê các file có đuôi theo yêu cầu:

![Exported image](Exported%20image%2020240225113003-2.png)  
![Exported image](Exported%20image%2020240225113003-3.png)  

- **Stream trong Java:**

![Exported image](Exported%20image%2020240225113003-4.png)  
  
  

- **Byte Stream(FileInputStream & FileOutputStream):** **làm việc với từng bytes một(8 bit)**
- Extends từ OutputStream và InputStream.
- Thường được dùng để đọc dữ liệu từ các File nhị phân nguyên bản(_Raw-binary-file_).
- Có cơ chế 3 giai đoạn:

+ Split: Nguồn dữ liệu vào được phân tách vào Stream bởi _Spliterator-Interface._

+ Apply: các phần tử trong Stream được xử lý.

+ Combine: sau khi các phần tử được xử lý, chúng lại tập hợp lại tạo ra 1 kết quả duy nhất.

- Nếu file không tồn tại thì tung exception(output-destination không có thì sẽ được tạo mới, nếu một đã tồn tại thì tung FileAlreadyExistsException).
- **OutputStreamWriter & InputStreamReader:**
- Extend từ Writer
- Hỗ trợ charSet kiểu String để mã hóa đầu ra theo UTF-8 hoặc UTF-16

  
![Exported image](Exported%20image%2020240225113003-5.png) ![Exported image](Exported%20image%2020240225113003-6.png)  

  
- **Characte****r Stream(FileReader & FileWriter):** **làm việc với 2 bytes**
- Extends từ OutputStreamWriter và InputStreamReader.
- Java.io.FileReader & java.io.FileWriter.
- Hỗ trợ Unicode.
- Cũng có cơ chế 3 giai đoạn như ByteStream.
- Không có hàm readAll.
- Nếu file không tồn tại thì tung exception(output-destination không có thì sẽ được tạo mới, nếu một đã tồn tại thì tung FileAlreadyExistsException).
  

  
![Exported image](Exported%20image%2020240225113003-7.png)  

- **ObjectInputStream & ObjectOutputStream:**
- ObjectInputStream chủ yếu được sử dụng để đọc data được ghi bởi ObjectOutputStream.
- ObjectOutputStream chuyển đổi các Object Java thành các Stream tương ứng(Serialization).
- ObjectInputStream chuyển đổi các Stream trở lại thành các Object tương ứng (Deserialization).
- Khi sử dụng ObjectOutputStream chỉ ghi các đối tượng có thể được chuyển đổi Serialization(Object phải implements Serialization).
- Sau khi thực hiện đọc và ghi xong phải đóng bằng close(), tránh hao phí tài nguyên.

  
  

- **BufferStream(****BufferedInputStream,BufferedOutputStream & BufferedReader, BufferedWriter****)**
- Đọc và ghi dữ liệu từ 1 vùng bộ nhớ buffer tạm thời
- BufferedInputStream & BufferedOutputStream: thực hiện ghi và đọc giống bytesStream
- BufferedReader & BufferWriter: thực hiện ghi và đọc giống characterStream
- PrintWriter: thực hiện ghi
- Sử dụng kèm với try with source: giúp bỏ đi bước tạo gán null và close()
- ![Exported image](Exported%20image%2020240225113003-8.png)
- Có thêm hàm readLine và write(String), write(Object) để đọc một dòng, ghi một dòng, ghi đối tượng.
- BufferdWriter thì không thê viết được đối tượng còn PrintWriter thì có thể viết được mọi thứ

  
![Exported image](Exported%20image%2020240225113003-9.png)  

  
![Exported image](Exported%20image%2020240225113003-10.png)  
![Exported image](Exported%20image%2020240225113003-11.png)  
![Exported image](Exported%20image%2020240225113003-12.png)- **Java NIO : Path, Paths, Files**
- Java.nio.file.Path : cho phép xác định vị trí file trong hệ thống lưu trữ file, là một interface
- Java.nio.file.Paths: Cho phép biến String hoặc URI thành Path
- Java.nio.file.Files : Cho phép thực hiện các thao tác với file và thư mục
    
    - ![Exported image](Exported%20image%2020240225113003-13.png)
- Phương thức get để tạo 1 path chưa xét tính đúng sai
    
    - ![Exported image](Exported%20image%2020240225113003-14.png)
- Nếu sử dụng hàm resolve để ghép với 1 đường dẫn tuyệt đối khác thì ưu tiên đường dẫn tuyệt đối phía sau
    
    - ![Exported image](Exported%20image%2020240225113003-15.png)
    - ![Exported image](Exported%20image%2020240225113003-16.png)
    
    - ![Exported image](Exported%20image%2020240225113003-17.png)
  

  
  
  
  
  
  

- **StandardOpenOption: java.nio.file.StandardOpenOption (NIO2)**
- CREATE: sẽ bỏ qua khi chạy trương trình tạo file không được(file đã tồn tại)
- CREATE_NEW: sẽ fail và tung exception khi chạy chương trình tạo file không được(file đã tồn tại)

![Exported image](Exported%20image%2020240225113003-18.png) ![Exported image](Exported%20image%2020240225113003-19.png)  

- WRITE: ghi đè lần lượt từ đầu số kí tự của bản ghi mới lên số kí tự của bản ghi cũ.
- TRUNCATE_EXISTING: nếu file đang mở ở chế độ write thì sẽ cắt toàn bộ độ dài dữ liệu về 0, mở ở chế độ read thì bị bỏ qua
- DELETE_ON_CLOSE : sau khi file đóng thì xóa file luôn
- Reader thì chỉ đọc, không thể sử dụng các StandardOpenOption

![Exported image](Exported%20image%2020240225113003-20.png)  
  

- WriteObject thì object phải được implements Seriallizable interface(ở đây là 1 list và 1 list đó cũng là đối tượng)

![Exported image](Exported%20image%2020240225113003-21.png)  

- ReadObject:
- Đọc hẳn 1 list cũng là 1 object

![Exported image](Exported%20image%2020240225113003-22.png) ![Exported image](Exported%20image%2020240225113003-23.png)