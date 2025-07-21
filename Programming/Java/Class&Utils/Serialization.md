---
created: 2024-02-25T11:30
updated: 2023-11-22T22:06
tags:
  - Java
---
## Definition:
- `Serializable`(tuần tự hóa) trong Java là một cơ chế giúp chuyển đổi trạng thái của 1 Object vào 1 `ByteStream` sao cho `ByteStream` này có thể chuyển đổi ngược trở lại thành một Object.
- Quá trình chuyển đổi từ `ByteStream` thành Object được gọi là `Deserialization`.
- Một Object thực hiện được `Serialization` thì phải implements interface `java.io.Serializable` do khi trao đổi data giữa các module khác nhau thể hiện dưới dạng byte chứ không phải Object.
- Quá trình này được vận hành độc lập với bất cứ nền tảng nào.

  
> ![Exported image](Exported%20image%2020240225113010-0.png)  
## Khi nào một class được xem là Serializable thành công?
- Những Object implements `java.io.Serializable` có thể chuyển đổi thành Stream.
- Tất cả các trường dữ liệu trong class phải `Serializable`. Nếu không phải được đánh dấu tạm thời - `transient`.
- Có thể thực hiện `Serializable` và `Deserializable` một Object bằng các class `ObjectInputStream` và `ObjectOutputStream`.
## Lưu ý:
- Trong java, quy ước khi một Object được tạo ra, tệp của Object đó sẽ có phần mở rộng là .ser
- Khi JVM không thể tim thấy mã bytecode của class trong Object, JVM sẽ tung ra `ClassNotFoundException`.
- Thuộc tính transient, static không thể `Serialization`.
- Toàn bộ thuộc tính của đối tượng phải được implements `Serializable`. Nếu không sẽ bị báo lỗi `java.io.NotSerializableException`
- Khi `Deserialization` hàm khởi tạo của Object đó sẽ không được gọi.