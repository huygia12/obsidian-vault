---
created: 1970-01-01T08:00
updated: 2024-03-28T16:46
tags:
  - SpringBoot
  - Java
---
## Concept :
 - *IoC Container* : tạo và quản lý các module. IoC container của Spring gọi là *Application context*.
 - *Bean*:  Là những module chính được IoC container tạo ra.

## Mechanism :
- Spring boot sử dụng các annotation để đánh dấu lên class, chỉ ra rằng class đó là 1 module : @Component, @Repository, @Controller, @Service,...
- Trong runtime, class được đánh dấu là Bean sẽ được tạo 1 object Singleton và bỏ vào IoC container.
- Khi cần thì kiểm tra xem đã có Bean chưa và lấy ra injection vào Bean cần nó.

## Implement :
- `@Autowired` : đặt tại vị trí muốn inject trong Class để Spring tự động tìm và inject. Cách này là không được khuyến khích dùng.
- `@Required` : phải luôn gọi để inject.
- `@Primary` : ưu tiên Bean này thực hiện injection.
- `@Qualifier("")`: chỉ định rõ tên Bean cụ thể được inject.
- `@Scope("prototype")` : Tạo mới mỗi lần sử dụng bean.
- `@Configuration` : đánh dấu là nơi định nghĩa các Bean.
- `@Bean`: Đánh dấu trên method đây là Bean và cần được đưa vào Context. nằm trong class có đánh dấu @Configuration.
- `@Value`: Được sử dụng trên thuộc tính của Class, có nhiệm vụ lấy thông tin từ file properties(yaml) và gán vào biến.