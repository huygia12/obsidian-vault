---
created: 2024-02-25T11:31
updated: 2023-02-17T13:17
---
/* Một class không thể kế thừa nhiều class được, nếu bạn không chỉ định lớp cha kế thừa cho class đó thì lớp đó sẽ tự động kế thừa lớp object */

  

/* object class sẽ giúp bạn khai báo trước một đối tượng mà bạn còn chưa biết đối tượng gì, vào tình huống cụ thể bạn sẽ ép kiểu về các lớp con cụ thể tương ứng */

  

// Object class chứa các giá trị chung hữu hiệu nhất cho các lớp còn lại :

  

/* public final Class getClass() : trả về một class chứa đựng các thông tin được xây dựng liên quan đến đối tượng đang gọi */

Eg: HinhTron hinh Tron = new HinhTron();

system.out.println("Thong tin doi tuong Hinh Tron: "+hinhTron.getClass().getName());

  

/* int hashCode(): trả về một giá trị hash code, có thể dùng như giá trị phân biệt các đối tượng với nhau*/

  

/* boolean equals(Object obj) : giống như equals bên string(thực chất string có một phần Override phương thức của class object); hàm này trả về giá trị boolean nếu hai đối tượng này giống nhau, không phải do được tạo ra từ cùng một lớp mà chúng có **giá trị tham chiếu** như nhau(có chung hashcode) */

  

/* Object clone(): khởi tạo và trả về một bản sao của đối tượng được gọi, nhưng nếu muốn dử dụng thì phải override lại từ lớp Object vì Object đang để access modifier của phương thức này là protected */

  

|   |   |
|---|---|
|/* String toString(): phương thức này giúp trả về một kiểu chuỗi diễn đạt cho đối tượng này; nội dung là sự kết hợp của chuỗi|(getClass().getName()+"@"+Integer.toHexString(hashCode()))|

Khi gọi phương thức này **không cần viết tường minh** là .toString()*/

  

/*void finalize(): có thể được override lại phương thức này để khai báo vào đó các hành động giải phóng các tài nguyên đang dùng trước khi bộ dọn rác garbage collection tiến hành dọn dẹp đối tượng không còn được sử dụng này ; Phương thức này được gọi tự động khi muốn giải phóng các tài nguyên liên quan đến đọc file, kết nối mạng …*/

  

// Còn một số phương thức khác như notify(), notifyAll(), wait()….