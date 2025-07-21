---
created: 2024-02-25T09:26
updated: 2023-11-09T15:59
---
- Thông tin về User:7 trường
- Username: tên đăng nhập, phân biệt hoa/ thường, nên dùng chữ thường.
- Password: lưu chuỗi pw đã hash, nếu có sd /etcshadow thì ở đây sẽ là chữ x.
- User ID:: hệ thống dùng User ID để phân biệt người này với người khác.
- Group ID: đây là Primary Group của user này.
- Comment: mô tả cho User.
- Home-Directory: thư mục home của từn user, thường sẽ nằm trong /home/tenuser.
- Shell: tên chương trình sẽ thưucj thi ngay sau khi user login vào. Nếu không có shell user sẽ không thể login. Mặc nhiên trên Linux sẽ dùng bash shell ở đây.
  
- Thông tin về Group: được lưu trong /etc/groups và /etc/gshadows.
![Exported image](Exported%20image%2020240225092654-0.png)  
- Công cụ quản lý tài khoản: 4 file chính quản lý người sử dụng:
![Exported image](Exported%20image%2020240225092654-1.png)  
  
- Quản lý CLI(User and Group):
![Exported image](Exported%20image%2020240225092654-2.png)