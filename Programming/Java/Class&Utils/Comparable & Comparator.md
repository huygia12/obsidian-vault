---
created: 2024-02-25T11:31
updated: 2023-04-18T20:56
---
-Sắp xếp: ten_list.sort() và Collections.sort()

//compareTo: Cái nào độ ưu tiên cao hơn thì trả về số âm và ngược lại, nếu tương đương nhau thì trả về 0

//compare: vẫn như compareTo nhưng truyền vào hai tham số để so sánh

  

// Comparable: tạo class cần phải implement comparable<ten_class>

Package: java.lang

Muốn sắp xếp theo attribute nào thì override lại compareTo để so sánh thuộc tính đó. Sử dụng hết trong một class để thực hiện so sánh các thuộc tính, nếu muốn thứ tự sắp xếp khác thì phải xóa code đi viết lại(bất tiện trong một số TH).

  

// Comparator: tạo class cần phải implement comparator<ten_class>

Package: java.util

Tách riêng ra từng class để override lại riêng lẻ các compare để so sánh attributes. Sau đó có thể sử dụng thenComparing() để tùy chỉnh thứ tự của từng loại sắp xếp(nếu muốn đảo ngược thì dùng reverse()).

Có thể dùng kết hợp với toán tử lambda để rút gọn đoạn code, không cần tạo nhiều class.

![Exported image](Exported%20image%2020240225113131-0.png)  
![Exported image](Exported%20image%2020240225113131-1.png)