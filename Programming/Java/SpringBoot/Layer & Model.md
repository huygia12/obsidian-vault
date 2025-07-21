---
created: 1970-01-01T08:00
updated: 2024-03-12T10:32
tags:
  - Java
  - SpringBoot
---
## Three tier :
- 1 mô hình tổ chức source code phổ biến trong Spring Boot.
- Trong đó, 1 ứng dụng được chia làm 3 tầng (tier hoặc layer) :
	- ***Presentation layer*** : tương tác với người dùng bằng View, Controller (trong `MVC`) hoặc API (nếu có).
	- ***Business logic layer*** : chứa toàn bộ Logic của chương trình, các đa số code nằm ở đây.
	- ***Data access layer*** : Tương tác với Database, trả về kết quả cho Business logic layer.

- Cách tổ chức code:
	- Service : chứa các business logic code.
	- Repository : đại diện cho Data access layer.

>![[Pasted image 20240309211115.png]]

## Combination to Spring Boot App :

- Các module của mô hình `MVC` được sử dụng ngầm trong Spring Boot.
- Kết hợp hai mô hình :
	- *Controller* : trả về View (dưới dạng HTML), hoặc Model thể hiện dưới dạng API cho View (được viết bằng React, Angular...).
	- *Service* : chứa các code tính toán, xử lý. Khi Controller yêu cầu thì Service tương ứng sẽ được gọi để trả lại data (hoặc model).
	- *Repository* : trực tiếp tương tác, đọc ghi data trong DB rồi trả cho Service.

>![[Pasted image 20240309212543.png|600]]

## Work flow :
- Data sau khi được Repository lấy ra từ DB được hệ thống `ORM` (`JPA` như `Hibernate`) mapping thành các object trong Java. Các object này được gọi là *Entity*.
- Service nhận Entity, thực hiện các thêm bớt, tính toán rồi biến Entity thành *Model*. Tiếp tục trả lại cho Controller.
- Controller nhận được Model, nó sẽ return cho View. Có 2 cách, một là dùng template engine pass dữ liệu Model vào trang HTML, rồi trả về cục HTML (đã có data) cho Client. Cách còn lại là gửi qua API, view tự parse ra và hiển thị tương ứng.

## Data classify :
-  Dữ liệu được chia thành 2 loại theo scope:
	- Public : trao đổi, chia sẻ với bên ngoài qua Rest API hoặc giao tiếp với các service khác trong micro-service. Data lúc này ở dạng `DTO`.
	- Private : dùng trong nội bộ ứng dụng, Data lúc này nằm trong các Domain model hoặc Entity.
- Dữ liệu có 3 dạng :
	- `DTO` (Data transfer object) : chuyển giữa client-server hoặc giữa các service trong micro-service. Giúp giảm bớt info không cần thiết và tăng độ bảo mật.
	- Domain model : các class làm tham số đầu vào cho service tính toán.
	- Entity : có thể mao với DB như 1 table. Chỉ có Entity mới đại diện cho data trong DB.

>[!alert] quy tắc thiết kế chung:
>- *Web layer* : chỉ nên xử lý DTO, đồng nghĩa với việc các Controller chỉ nên nhận và trả về dữ liệu là DTO.
>- *Service layer* : nhận vào DTO(từ controller gửi qua) hoặc Domain model(từ các service nội bộ khác). Dữ liệu được xử lý cuối cùng được Service trả về Web layer dưới dạng DTO.
>- *Repository layer* : chỉ thao tác trên Entity vì là đối tượng có thể mapping vào DB.

##  Model mapping:
- Việc convert giữa các dạng data(giữa DTO và Entity) được gọi là model mapping.