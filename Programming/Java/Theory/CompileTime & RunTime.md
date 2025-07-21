---
created: 2024-02-25T11:30
updated: 2023-10-30T16:04
tags:
  - Java
---
- Trong java, để chạy một chương trình phải trải qua hai bước, compilation và sau đó là execution.
![Exported image](Exported%20image%2020240225113038-0.png)  
- **Compile-Time**: Trong CompileTime, _javac_(javaCompiler) nhận sourceCode(.java File) và kiểm tra nếu có bất kỳ lỗi do Syntax, Type-checking, hoặc Semantic trong chương trình.
    
    - Nếu không bị lỗi thì Compiler tạo ra file .class(byteCode) cho file .java trước đó.
    - Nếu có lỗi Compilation, java Compiler hiển thị lỗi đó trong cửa sổ lệnh(eg cmd). Lỗi này được gọi là CompileTimeError.
      
    
- **Run-Time**: Sau khi compile và thực hiện execute trên IDE hoặc chạy câu lệnh java project.java trên cmd để chạy chương trình. Nó chỉ kết thúc khi có đầu ra của chương trình được tạo hoặc Runtime-Error được quăng ra.
    
    - RunTimeError: Divide by zero….
    - JVM tải file .class trừ bộ nhớ và chạy để tạo đầu ra của chương trình.
- JVM là nền tảng ảo nằm trên RAM. Các thành phần của nó:

+ **Class-Loader** tải file .class lên RAM.

+ **Byte-Code-Verifier**: kiểm tra nếu có bất kỳ xung đột hạn chế truy cập(access restriction ciolations) nào trong code không(Đây là một trong những lý do chính tại sao java an toàn).

+ **Execution-Engine**: chuyển ByteCode sang MachineCode có thể chạy được.

  
- Lệnh thông báo hệ thống nơi tìm chương trình JDK('path': đường dẫn đến folder chứa file java muốn execute):

  
  
  

_C:\'__path__'> set path=%path%;C:\Program Files\Java\jdk1__.5__.0_09__\__bin_