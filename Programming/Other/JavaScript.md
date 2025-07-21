---
created: 2024-05-17T15:53
updated: 2024-06-14T00:26
---
## New concept:
- `Destructuring Object or Array`
- `Rest Operator`: Dùng được với Array.
	- Dùng để hứng hết tất cả giá trị còn lại.
- `Spread Operator` : Giống syntax với `Rest`, có thể dùng với cả Object và Array. 
	- Dùng để liệt ra hết tất cả các giá trị, thuộc tính.(có thể ghi gía trị nếu trùng tên atr)
- `Template literals` : Cho phép kết hợp giữa string và javascript expression liền mạch
	- Sử dụng \` \` để bao quanh chuỗi kết quả. 
	- Sử dụng `${}` để bao quanh javascript expression.
- `Short circuit` : falsy(false, 0, undefined, null, ""); truthy thì ngược lại.
	- && : nếu falsy thì trả về vế đầu và ngược lại.
	- || : nếu falsy thì trả về vế sau và ngược lại.
	- ?? : nếu giá trị thứ nhất là null hoặc falsy thì trả về giá trị thứ hai và ngược lại.
- `Optional chaining` : Trong 1 chaining các thuộc tính được gọi, nếu function trước dấu ? là undefined hoặc null thì trả luôn tại đó, nếu khác thì gọi tiếp.

## Asynchronous:
- `forEach` không hỗ trợ `async/await` giống như `map`, nó sẽ không chờ promise hoàn thành để tiếp tục vòng lặp tiếp theo.
- `Promise.all(promises)` đợi tất cả các promise hoàn thành để trả về 1 mảng các kết quả.