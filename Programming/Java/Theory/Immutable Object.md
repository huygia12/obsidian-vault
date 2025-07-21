---
created: 2024-02-25T11:31
updated: 2023-04-12T11:26
---
- **Immutable Object:** là những object không thay đổi giá trị các thuộc tính, trạng thái của nó sau khi khởi tạo.
- ![Exported image](Exported%20image%2020240225113135-0.png)
- Khi tạo một List các immutable object rồi gán nó sang list khác(sử dụng Collections.copy hoặc truyền thẳng vào constructor) thì các phần tử trong list đó dù có thay đổi cũng không ảnh hưởng giá trị đến list còn lại(điều này là ngược lại với mutable object).