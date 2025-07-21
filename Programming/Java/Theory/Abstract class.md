---
created: 2024-02-25T11:30
updated: 2024-01-18T18:57
---
- **Abstract class****:** là một class được khai báo với từ khóa abstract, các phương thức chỉ được khai báo dưới dạng khuôn mẫu.
- Abstract method có thể chứa các abstract method và các method thông thường.
- Abstract method không thể khởi tạo trực tiếp (một số có thể khởi tạo gián tiếp thông qua method của chúng).
- Class thông thường không thể có abstract method.

  
  

- **Abstract method**: là một method mà không có thân hàm
  
- Class con kế thừa từ abstract class phải override lại abstract method.
- Một class chứa abstract method thì bắt buộc nó phải là abstract class.
- Eg:
- Khi một class kế thừa 1 interface thì nó sẽ kế thừa toàn bộ những phương thức abstract của interface đó.
- Access modifier luôn là public cho dù có khai báo rõ hay không.
- Thuộc tính luôn là public static final cho dù có khai báo rõ hay không.
- Các phương thức đều là phương thức trừu tượng, đều có modifier là public abstract cho dù có khai báo rõ hay không.
- Không thể khởi tạo và không có hàm khởi tạo.
- Hỗ trợ đa kế thừa.
- Interface được khai triển từ phía class.
- Class mô tả hành vi và thuộc tính của đối tượng, còn interface chứa các hành vi mà 1 class triển khai.
  

  
![Exported image](Exported%20image%2020240225113000-0.png)  
![Exported image](Exported%20image%2020240225113000-1.png) ![Exported image](Exported%20image%2020240225113000-2.png) ![Exported image](Exported%20image%2020240225113000-3.png)  
  
  
![Exported image](Exported%20image%2020240225113000-4.png)  
![Exported image](Exported%20image%2020240225113000-5.png)