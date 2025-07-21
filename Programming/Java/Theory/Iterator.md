---
created: 2024-02-25T11:30
updated: 2023-10-28T23:02
---
- **Khái niệm:**
- Là 1 Design pattern dựa vào Interface
- Iterator là cách hiệu quả để duyêtn một Object.
- Giấu thuật toán bên trong khỏi Client.
- Giúp ta tận dụng được cú pháp For-Eachđể đơn giản hóa việc lặp qua đối tượng trong vòng For-Each.

  

- **Vấn đề:**
- Việc chỉnh sửa một Collection khi đang thực hiện lặp qua Collection đó sử dụng _Iterator_ là không được chấp thuận bởi hầu hết các lớp trong Collection. Java gọi việc thực hiện này là "Concurrent modification". Exception này có thể được tung ra bởi các phương thức đã phát hiện ra việc sửa đổi đồng thời một đối tượng khi việc sửa đổi đó là không được cho phép.
    
    - Iterator are fail-fast: Nếu thực hiện sửa đổi Collection bất kì lúc nào sau khi Iterator được tạo lập(trừ khi sử dụng hàm sửa đổi của Iterator cung cấp) thì "ConcurrentModificationException" sẽ được tung ra. -> Vì đó mà nếu sửa đổi đồng thời thì Iterator sẽ thất bại nhanh chóng và gọn gàng, thay vì ảnh hưởng đến một thời điểm xác định trong tương lai.
    - Fail-Fast Behavior should be used only to detect bugs.
      
    
- Ngăn chặn lỗi Concurrent-modification: Khi có thể, hạn chế các tham chiếu đến Collection object(tạo Collection là private object hoặc biến Local), không trả về tham chiếu đến Collection hoặc Iterator của nó từ phương thức. Giúp xoát dễ dàng hơn mọi chỗ mà Collection có thể bị sửa đổi. Nếu Collection được thao tác với đa luồng, luyện tập để đảm bảo rằng việc truy cập đến Collection được đồng bộ hóa và khóa đúng cách.