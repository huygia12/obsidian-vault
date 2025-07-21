---
created: 1970-01-01T08:00
updated: 2024-05-13T10:53
tags:
  - SpringBoot
  - Java
  - BackEnd
---
## Project convention
- Refresh token chỉ được dùng 1 lần, được lưu thành mảng trong Database.
## Authen-service
#### Token logic
- Refresh mechanism : refresh token có thể đang expired hoặc không.
	1. Kiểm tra state xem token hợp lệ hay không (signature).
	2. Thực hiện xóa luôn refresh token hiện tại (loop qua 1 lần mảng active refresh token để kiểm tra độ dài) và kiểm tra hacker xâm nhập. Nếu có phát hiện thấy refresh token (trường hợp này mặc định được verify do user gửi request) thì thực hiện cập nhật lại mảng active refresh token.
		- Nếu không phát hiện thấy refresh token trong mảng (hacker đã có được refresh token) thì clear mảng. Lúc này tất cả nơi đã login tài khoản của user phải thực hiện login lại.
	3. Tạo mới 2 token và thực hiện response 200.

## Manifest
```
config_map : chua bien moi truong
deployment: tao ban sao -> pod -> container
service: tao network
namespace: filter
secrete: chua bien moi truong secrete
```
