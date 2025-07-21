---
tags:
  - Hosting
  - Web
created: 2024-02-24T17:25
updated: 2024-03-03T14:33
---
	# Getting Started :

- Là một ứng dụng tạo ra 1 đường hầm từ desktop, localhost đi qua hệ thống Firewall//Nat,, giúp từ ngoài Internet truy cập vào một trang Web(máy chủ http) đang chạy thử trên máy mà không nhất thiết phải triển khai web trên 1 server thực sự).
- Các kết nối TCP được thực hiệ tương tự
##### Các tính năng (giới hạn trong gói Free) :
* Cho tạo các đường kết nối http/tcp với Url sinh ngẫu nhiên.
* Chỉ 1 process ngrok chạy trực tuyến.
* Tối đa 4 Tunnel trên Process.
* 40 kết nối trên phút.
##### Cú pháp tạo 1 Tunnel :
```Shell
ngrok http port_number
```

>[!note]
> Khi ngrok đang chạy sẽ cung cấp 1 site quản lý, giám sát ở địa chỉ : 
> `http:/127/0.0.1.4040/`
> Tại đây có thể biết được các thông số, các kết nối đến web.

##### Đặt user/pass yêu cầu cho truy cập từ ngoài Internet :
-  Pass phải lớn hơn hoặc bằng 8 ký tự.

```Shell
ngrok http --basic-auth port_number
```
