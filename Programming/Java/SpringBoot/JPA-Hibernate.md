---
created: 1970-01-01T08:00
updated: 2024-03-09T20:53
tags:
  - Java
  - SpringBoot
---
## Definition:
- JPA(Java Persistence API) là 1 đặc tả, tiêu chuẩn do Oracle phát triển và trở thành 1 phần của Java EE, nó là 1 tập các interface và không có triển khai cụ thể nhưng khi cài spring-jpa thì mặc định hibernate sẽ được sử dụng.
- Hibernate là 1 ORM mã nguồn mở
	- Hibernate sử dụng `connection pool` để tối ưu hóa kết nối cơ sở dữ liệu thay vì đóng mở kết nối mỗi khi truy cập Database, giữ 1 nhóm các kết nối có sẵn để tái sử dụng. 
	- `HikariCP` là 1 implementation của `connection pool` có hiệu suất cao, tiêu thụ tài nguyên thấp, dễ cấu hình.
