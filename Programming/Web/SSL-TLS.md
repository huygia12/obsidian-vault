---
tags:
  - Web
created: 2024-02-26T01:27
updated: 2024-03-03T13:45
---

# Concept :
- ***HTTPS*** : là 1 giao thức ở tầng [[TCP-IP#^b34392|Aplication]], được xây dựng bên trên giao thức giao vận an toàn SSL/TSL thay vì TCP. Khi sử dụng giao thức HTTPS các HTTP Request và HTTP Reponse hoàn toàn không có gì thay đổi, chỉ có tầng bên dưới là data được truyền đi bằng giao thức SSL (nội dung được mã hóa).   
- ***Asynmetric encryption***: Server holds two keys (public key and private key) public key encryption and private key for decryption (or maybe in reverse). 
- ***SSL (Secure Socket Layer)*** : tiêu chuẩn bảo mật, mã hóa giữa trình duyệt và web server, giúp data được toàn vẹn, riêng tư và bảo mật. 
- ***TSL (Transport Layer Security)***: Phát triển từ SSL.
- ***CA (Certificate Authority)*** : đơn vị cấp phát chứng thực các loại chứng thư số cho user, server, doanh nghiệp, phần mềm và mã nguồn. 
- ***Authorization chain*** :

- ***Certificate authorities***:  

# Loại chứng chỉ SSL : 
|                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Domain Validation (DV SSL)       | - Chứng chỉ cơ bản về dễ đạt được nhất. Trong quá trình xác thực, nhà cc chứng chỉ kiểm tra xem người yêu cầu chứng chỉ có quyền kiếm sóat với tên miền được liên kết với chứng chỉ hay không. <br>- Quá trình xác thực được thực hiện thông qua việc gửi 1 email hoặc xác thực qua DNS hoặc tệp văn bản trên trang web. <br>- Thích hợp cho các web cá nhân, blog, web không yêu cầu nhiều sự xác thực.                                                                           |
| Organization Validation (OV SSL) | - Quá trình xác thực bao gồm việc xác minh quyền sở hữu tên miền(giống với DV), xác minh doanh nghiệp đăng ký với tên và địa chỉ của trụ sở chính. <br>- Dành cho các tổ chức và doanh nghiệp có độ tin cậy cao.                                                                                                                                                                                                                                                                   |
| Extended Validation (EV SSL)     | - Chứng chỉ xác thực mở rộng, có độ tin cậy cao nhất. <br>- Quá trình xác thực bao gồm nhà cc chứng chỉ thưucj sự kiểm tra thông tin về tổ chức, xác minh rõ ràng về sự tồn tại pháp lý của tổ chức và quyền lực của người yêu cầu chứng chỉ. <br>- Dành cho các doanh nghiệp và tổ chức đang hoạt động. Tuân thủ nghiêm ngặt các quy định của tổ chức CA trong quá trình xác minh doanh nghiệp. Web được hiển thị 1 biểu tượng màu xanh lá cây hoặc thanh địa chỉ màu xanh dương. |
