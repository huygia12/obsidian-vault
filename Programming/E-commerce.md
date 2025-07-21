---
created: 1970-01-01T08:00
updated: 2024-05-31T18:59
---
## Concept:
- Actor: 
	- `User`: khách hàng đã đăng nhập vào hệ thống (số nhiều).
	- `Admin`: người bán hàng (số nhiều).
- Danh mục(Điện thoại, camera, máy tính,...): 
	- Dùng để hiển thị trên thanh `navbar`, khi `User` hover vào thì hiển thị danh sách mục và có thể chọn để redirect sang 1 page tương ứng với mục đó.
	- Dùng để lọc các sản phẩm theo danh mục này.
	- Breadcrumb: `Trang chủ / ten_danh_muc`
	- End point: `ten_danh_muc` 
- Nhà sản xuất(Samsung, apple,...) 
	- Sau khi đã redirect vào page của 1 danh mục nhất định rồi thì có thể chọn hãng để tiếp tục lọc.
	- Dùng để lọc sản phẩm theo hãng này
	- Breadcrumb: `Trang chủ / ten_danh_muc / hang `
## Function overview:
#### Admin:
- Sửa thông tin cá nhân.
- Dashboard:
	- Hiển thị các ô:
		- Tổng số đơn hàng đang chờ được xét duyệt.
		- Tổng số đơn hàng đang được vận chuyển.
		- Tổng số sản phẩm hiện đang có.
		- Tổng số doanh thu tháng này.
	- Hiện thị mẫu 1 đơn hàng chờ được xét duyệt.
	- Biểu đồ danh thu.
	- Hiển thị mẫu 5 danh sách khách hàng mới.
- Quản lý danh mục và nhà sản xuất:
	- Thêm danh mục:
		- Mô tả: nhập vào tên danh mục.
	- Sửa:
		- Mô tả: sửa tên danh mục.
	- Xóa danh mục:
		- Điều kiện: chỉ xóa thành công khi danh mục chưa có sản phẩm nào.
	- Thêm nhà sản xuất: 
		- Điều kiện: chọn vào 1 danh mục để hiển thị danh sách nhà sản xuất.
	- Xóa nhà sản xuất: 
		- Điều kiện: chọn vào danh mục để hiển thị danh sách nhà sản xuất, chỉ xóa thành công khi không có sản phẩm vào của nhà sản xuất này.
- Quản lý mặt hàng:	
	- Thêm hàng:
		1. Nhập vào các trường giá trị chung.
		2. Thực hiện thêm các trường giá trị riêng (được tính là 1 mặt hàng khác).
		3. Xác nhận.
	 - Xóa mặt hàng.
	 - Sửa mặt hàng.
	- Bật giảm giá.
- Quản lý người dùng:
	- Thêm, sửa người dùng.
		- Không thể sửa thông tin admin khác nhưng có thể xóa.
	- Xóa: 
		- Điều kiện: không cho xóa người dùng đang có đơn hàng.
	- Khóa người dùng:
		- Điều kiện: có thể khóa admin khác.
- Quản lý đơn hàng:
	- Sửa trạng thái đơn hàng:
		- Điều kiện: chọn xem đơn hàng.
	- Xoá đơn hàng:
		- Đổi trạng thái đơn hàng thành `abort`, bên phía client thì hiển thị thông báo trong mục thông báo là bị hủy từ phía người bán.
- Phản hồi khách hàng:
	- Xem đánh giá của khách hàng
	- Xóa đánh giá của khách hàng.
	

## Todo
- Filter-product-page: 
	- Số lượng của sản phẩm sau khi query
	- Sắp xếp theo tên
	- 
