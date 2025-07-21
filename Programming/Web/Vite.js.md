---
created: 2024-02-26T01:06
updated: 2024-05-30T13:49
---
# Concept :

# Under the hood:
- Dist : (distribution) được tạo ra khi chạy lệnh vite build, chứa các file sẽ được triển khai khi lên Production environment, tối ưu hóa và sẵn sàng để chạy. 
- Trong quá trình build vite sử dụng các kỹ thuật như minification[^1]  và tree shaking[^2]  giúp tăng hiệu suất tải trang và thời gian tải.
- Có hỗ trợ HMR (Hot module replacement) không cần tải lại trang trong quá trình development.
- Sử dụng ESBuild để biên dịch typescript (nhanh hơn so với babel hay tsc).


[^1]: Minification :  tối ưu hóa kích thước tệp.
[^2]: Tree shaking : loại bỏ mã không sư dụng để giảm kích thước ứng dụng.