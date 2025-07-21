---
created: 1970-01-01T08:00
updated: 2024-03-27T17:51
tags:
  - Java
  - DesignPattern
---
## Concept :
- Dependency injection là 1 *design pattern*.
- Nghĩa là tạo ra một *Abstraction Class* để Inject vào 1 *Object*, qua trình inject chỉ được thực hiện trong lúc *runtime*.

>*Principle* : Phải giảm sự phụ thuộc giữa các module. Biến mối quan hệ giữa chúng từ tight coupling thành loose coupling.

## Ways to inject dependency :
- Constructor Injection : 
- Setter Injection :
- Interface Injection : phải thực hiện implement một Interface có chứa một hàm dạng inject(xx) rồi gọi hàm.