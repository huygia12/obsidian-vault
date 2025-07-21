---
created: 2024-02-25T11:30
updated: 2023-11-07T10:50
---
- Tận dụng lại và mở rộng hơn các thuộc tính và phương thức có sẵn từ một đối tượng nào đó.
- Để thể hiện một lớp kế thừa từ một lớp nào đó bạn sử dụng từ khóa **extends**.
- Lớp cho kế thừa là **lớp cơ sở(base class), hay lớp cha (super class, parent class).** Còn lớp được kế thừa được gọi là **lớp dẫn xuất(derived class)** hay **lớp con(sub class, child class).**
- Một lớp chỉ được kế thừa từ một và chỉ một lớp cha mà thôi.
- Lớp cha mà đối tượng đang kế thừa này có thể kế thừa từ một lớp cha khác.
- Khi một lớp không khai báo kế thừa gì thì hệ thống mặc định nó đang kế thừa từ lớp **Object**
- **Lưu ý:**

**+** **Khi kế thừa một method và override lại trong class con thì chỉ khi kiểu dữ liệu trả về là con của kiểu dữ liệu được override, không thì không được thay đổi kiểu dữ liệu trả về.**

**+** **Quyền truy cập không chặt hơn phương thức được định nghĩa l****ại****(tác dụng phương thức không phải Private).**