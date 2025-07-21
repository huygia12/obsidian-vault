- Đều là các loại trình dịch ngôn ngữ chuyển đổi các đoạn mã lập trình sang ngôn ngữ máy.
  
- **Khác biệt giữa Compiler và Interpreter**:
- Khác biệt nằm ở quá trình chuyển đổi và thực thi:
    
    - Thông dịch là khi chạy chương trình, ngôn ngữ mới được dịch sang ngôn ngữ máy và thực thi.
    - Biên dịch là trước khi chạy, chương trình sẽ dịch toàn bộ thành mã máy rồi mới tiến hành thực thi.
![Exported image](Exported%20image%2020240225092711-0.png)  
- Nhận xét:

+ Ngôn ngữ thông dịch dễ thực hiện hơn do bỏ qua kiểm tra lỗi và tối ưu code thường được thực hiện trong quá trình compiled.

+ Hỗ trợ hoạt động đa nền tảng, mã nguồn có thể thực thi mọi lúc mọi nơi mà không cần biên dịch.

+ Tuy nhiên dộ tin cậy thấp hơn do không qua bước check-syntax tại quá trình compiler.

+ Tốc độ thực thi chậm hơn đáng kể so với các ngôn ngữ trình biên dịch.

+ Dễ bị dịch ngược code.

  
- **Ngôn ngữ C++**:
- Là ngôn ngữ lập trình biên dịch, Visual Studio là trình biên dịch và Windows là HDH.
    
    - Viết code C++ bằng Visual Studio và nhấn chạy.
    - Visual Studio dịch các file .cpp thành các file .dll và .exe
    - Windows sẽ thực thi các file .dll và .exe.

  
  
  
  

- **Ngôn ngữ Java**:
- Là ngông ngữ thông dịch điển hình. Người dùng viết mã nguồn bằng Netbean trên Linux và Run-code.
    
    - Viết Code java.
    - Netbean sẽ dịch các file .java thành file .class… hay còn gọi là java-byte-code.
    - Các file java-byte-code sẽ được thực thi bởi JVM(chính là trình thông dịch).
    - JVM chạy trên Linux.
- Ngoài ra còn có một số ngôn ngữ lập trình thông dịch phổ biến khác như là C# hoặc ngôn ngữ truy vấn T-SQL và PL/SQL(được SQL engine thực thi trên rất nhều hdh khác nhau sau khi được biên dịch).
  

  

|   |   |   |
|---|---|---|
|**Tiêu chí**|**Trình biện dịch**|**Trình thông dịch**|
|Đầu vào|Toàn bộ trường trình|Chỉ một dòng code|
|Đầu ra|Mã đối tượng trung gian|Không tạo ra bất kì mã đối tượng trung gian nào|
|Cơ chế hoạt động|Việc biên dịch sẽ phải hoàn thành công việc trước khi thực thi|Việc biên dịch và thực thi sẽ là đồng thời|
|Tốc độ|Nhanh hơn|Chậm hơn|
|Bộ nhớ|Yêu cầu bộ nhớ nhiều hơn do việc tạo mã đối tượng|Nó đòi hỏi ít bộ nhớ hơn vì nó không tạo mã đối tượng trung gian|
|Errors|Hiển thị tất cả các lỗi sau khi biên dịch, tất cả cùng một lúc|Hiển thị lỗi của từng dòng một|
|Phát hiện error|Rất khó khăn|Tương đối dễ|
|NNLT|C, C++, C#, Scala, typescript|PHP, Perl, Python, Ruby|