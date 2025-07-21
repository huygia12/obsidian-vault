
## Mô hình tổng quan
<div style="display: flex; width:100%;">
    <img src="Screenshot%20from%202025-03-17%2021-21-13.png" style="width: 50%; height: auto;" />
    <img src="Screenshot%20from%202025-03-17%2021-45-39.png" style="width: 50%; height: auto;" />
</div>


## Triển khai ứng dụng với mã hóa khối AES GCM:
### Tiền điều kiện:
- Secret key: mỗi người dùng khi đăng ký sẽ được sinh 1 khóa, lưu ở trong database dưới dạng được mã hóa.
- Master key: là duy nhất và lưu trong file `.env` ở phía back-end, cũng dùng thuật toán `AES-GCM` để mã hóa secret key.
- Client key: được dẫn xuất lại mỗi lần người dùng đăng nhập (dẫn xuất từ chính mật khẩu dạng plain-text của người dùng).

### Luồng có trong ứng dụng:
##### Đăng ký:
- Server nhận được request đăng ký từ phía client thì thực hiện sinh mới 1 `Secret key`. Mã hóa dữ liệu bằng nó và cuối cùng mã hóa chính `Secret key` bằng `Master key` lấy ra từ file `.env`. Mật khẩu cũng được mã hóa `Bcrypt`.
##### Đăng nhập: 
- Client gửi password dạng plain-text cho server. Sau khi đã kiểm tra bản mã hóa `Bcrypt` của mật khẩu plain-text và thấy hợp lệ, server dẫn xuất ra `Client key` để mã hóa `Secret key`. Gửi lại bằng response cho phía client.
- Client cũng  dẫn xuất ra `Client key` sau khi đã nhận response để lấy được `Secret key`.
##### Cập nhật thông tin:
- Client gửi 

### Vấn đề:
- Ứng dụng sẽ có nhiều hơn 1 role hay không?