---
created: 2024-02-25T11:30
updated: 2023-10-29T01:13
---
## Definition:
- **Generics**: là kiểu tham số hóa, có thể khiến cho lớp hoặc phương thức hoạt động được với nhiều kiểu tham số khác nhau
- **Generic entity**: Một class, interface hoặc method thực hiện tham số hóa.
- Generics chỉ hoạt động với mỗi kiểu dữ liệu tham chiếu (Reference Type), đặc biệt với mảng các kiểu dữ liệu nguyên thủy thì có thể được vì nó vẫn là kiểu dữ liệu tham chiếu.

![Exported image](Exported%20image%2020240225113044-0.png)  
## Advantages of Using Generics:
- **Code reuse**: ta có thể viết method/class/interface một lần và xử dụng nó với bất kỳ kiểu dữ liệu nào mà ta muốn.
- **Type safe**: generics khiến cho lỗi được tung ra ngay trong compile time thay vì trong runtime, ví dụ như ta tạo một collection chứa kiểu dữ liệu là String thì chỉ nhận mỗi String nhưng nếu không nêu rõ thì collection sẽ nhận hết dưới dạng object nhưng lúc lấy ra để cast về kiểu String thì sẽ sai ngay.
- **Individual Type casting is not needed**: không cần thực hiện cast về đúng kiểu dữ liệu mong muốn khi đã quy định kiểu dữ liệu đầu vào.
- **Implementing Generic Algorithms****:** có thể phát triển cùng một thuật toán cho tất cả các kiểu dữ liệu đầu vào.

## Vấn đề:
- Không thể tạo Generic Array trong Java.