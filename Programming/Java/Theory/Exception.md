---
created: 2024-02-25T11:31
updated: 2023-03-16T21:37
---
// Exception: làm phá vỡ luồng sử lý bình thường của một chương trình, hoặc có thể làm chết chương trìnnh.

  

// Hệ thống phân cấp ngoại lệ:

![Exported image](Exported%20image%2020240225113138-0.png)  

// Checked exceptions: xảy ra trong lúc biên dịch chương trình, bắt buộc người lập trình phải xử lý, không được phép bỏ qua.

Eg: IOException

FileNotFoundException

NoSuchFileException

  

// Unchecked exceptions: là ngoại lệ xảy ra trong lúc thực thi chương trình(runtime exceptions, không bắt buộc phải xử lý, bị bỏ qua trong quá trình biên dịch.

Eg: NullPointerException

NumberFormatException

ArayIndexOutOfBoundsException

DivideByZeroException

  

// Error: là những vấn đề nghiêm trọng liên quan đến môi trường thực thi ứng dụng hoặc hệ thống, làm chết chương trình.

Eg: OutOfMemoryError

VirtualMachineError

StackOverflowError

  

// Exception Handling: là cơ chế xử lý các lỗi runtime có thể duy trì luồng thực thi một cách bình thường của ứng dụng, quá trình này gọi là catch exception

//Sử dụng khối lệnh try..catch…fianlly

![Exported image](Exported%20image%2020240225113138-1.png)  

// Khối lệnh finally sẽ thực thi cho dù trước đó có return nhưng sẽ bị thoát bằng cáhc gọi system.exit()

![Exported image](Exported%20image%2020240225113138-2.png)  
  

// Từ kháo throw và throws

/*throws: sử dụng ngay đầu phương thức để báo hiệu cho nơi gọi phương thức đó biết rằng phương thức đang được gọi vó thể gây ra ngoại lệ*/

![Exported image](Exported%20image%2020240225113138-3.png)

/*throw: sử dụng trong thân của phương thức, mục đích để tung ra ngoại lệ ở bất kỳ vị trí nào có khả năng phát sinh ngoại lệ(bắt buộc phải có throw ở đầu hàm và ném ra ngoại lệ tương ứng)*/

![Exported image](Exported%20image%2020240225113138-4.png)  
  

// Tự định nghĩa ngoại lệ: do ngoại lệ của hệ thống là không đủ nên cần phải xây dựng thêm ngoại lệ: xây dựng class kế thừa từ class Exception và có tất cả các phương thức của class Throwable

![Exported image](Exported%20image%2020240225113138-5.png)  
![Exported image](Exported%20image%2020240225113138-6.png)  

/* Infinite loop caused by invalid input (InputMismatchException) using Scanner:

Khi một scanner ném ra InputMisMatchException, có nghĩa là input nhập vào không đúng kiểu dữ liệu và scanner không cho phép truyền vào, giữ lại và bị skip qua scanner đến method khác; ở đây thì sau khi giữ lại sẽ được đọc đi đọc lại làm cho exception bị quăng ra liên tục làm cho vòng lặp không thể kết thúc:

Solve: Dùng một scanner .next() hoặc .nextLine() để bắt chuỗi không hợp lệ và loại bỏ*/