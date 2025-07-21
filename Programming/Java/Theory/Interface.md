---
created: 2024-02-25T11:30
updated: 2024-05-01T22:05
tags:
  - Java
---
## Definition
- Là 1 tập hợp các abstract method.
- Class mô tả hành vi và thuộc tính của đối tượng, còn interface chứa các hành vi mà 1 class triển khai.
- Tên của interface thường chỉ khả năng làm gì hoặc hành động.

## Concept 
- Không thể khởi tạo, không có constructor.
- Khi implements thì phải triển khai toàn bộ abstract method của interface đó.
	- Attribute: public static final (luôn luôn).
	- Method: public abstract method.
- Hỗ trợ đa kế thừa.
```
interface <ten_interface> {
	// các thuộc tính
	// các phương thức
}
```

## Implement trực tiếp method trong interface
- Có thể implement method trong interface qua 2 cách:
	+ Sử dụng static method (method trong interface chỉ có thể là static hoặc abstract).
	+ Sử dụng từ khóa default.
		- Java 8 cung cấp từ khóa để đánh dấu default method.
		- Các class, interface nếu implements sẽ mặc định kế thừa default method đó.
		- Có thể override được lại.
  
## Functional Interface
- Java 8.
- Có duy nhất một abstract method, có thể có hoặc không có nhiều default(hoặc static) method.
- Thường được sử dụng để truyền object.
- Phần implementation của functional interface sẽ được triển khai theo nhiều cách(lambda expression, method reference, anonymous class hoặc tạo hẳn 1 class riêng biệt).

## References
[implementation-cua-functional-interface](https://blog.tonghoangvu.dev/cac-dang-implementation-cua-functional-interface)

```Java
@FunctionalInterface
interface Caculable{
	double calculate();
}

// Đặt interface làm Param và thực hiện gọi method đã được implement
public void printResult(Calculable func){
	System.out.println("Result: " + func.calculate());
}

// Truyền vào method
printResult(new Calculable(){
	@Override
	public double calculate(){
		return 3.14;
	}
})
```
  
