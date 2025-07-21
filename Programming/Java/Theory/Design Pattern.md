---
created: 2024-02-25T11:31
updated: 2023-05-01T15:26
---
## Creational pattern: 
- Gồm có: Factory Pattern, Abstract Factory, Builder, Prototype, Singleton.
- Cung cấp giải pháp tạo ra object và giúp che giấu logic tạo ra nó thay vì tạo trực tiếp, giúp mềm dẻo hơn khi tạo object theo tình huống nào đó.
#### Factory pattern: 
- Giúp "sản xuất đối tượng" mà che giấu đi logic tạo ra đối tượng đó. Được sử dụng khi có một class cha và có nhiều class con mà tùy theo trường hợp để khởi tạo một trong những class con đó.
    - Các thành phần: super-class, sub-classes, factory-class(dựa theo tham số đầu vào để tạo class con, thường sử dụng else if hoặc switch-case để xác định class con đầu ra)
#### Builder pattern:
- Chỉ khởi tạo những thuộc tính của đối tượng cần để sử dụng
    - Thành phần: Product(đối tượng có nhiều attribute phức tạp); Builder(abstract class hoặc interface khai báo phương thức dùng để khởi tạo đối tượng); concrete builder (kế thừa builder và cài đặt chi tiết cách tạo ra đối tượng, cung cấp các phương thức trả lại các Instance)
## Structural pattern: 
- Gồm có: Adapter, Bridge, Composite, Decorator, facade, flyweight, proxy.
- Giúp thiết lập các mối quan hệ giữa các đối tượng với nhau.
## Behavioral pattern:  
- Gồm có: Interpreter, Template Method, Chain of Responsibility, Command, Iterator, Mediator, Memento, Observer, State, Strategy, Visitor
- Cung cấp các giải pháp để thực hiện hành vi của đối tượng cũng như giữa các object với nhau.