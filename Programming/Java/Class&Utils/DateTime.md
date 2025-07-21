---
created: 2024-02-25T11:31
updated: 2023-03-20T23:19
---
// DATE TIME IN JAVA 5, 6, 7

![Exported image](Exported%20image%2020240225113137-0.png)  
![Exported image](Exported%20image%2020240225113137-1.png)  

// System.currentTimeMillis() : là một static method của class System, trả về khoảng thời gian tính bằng mili sec tính từ 1/1/1970 tới hiện tại, thường được sử dụng để đo khoảng thời gian thực hiện một đoạn code

![Exported image](Exported%20image%2020240225113137-2.png)  
  

//TimeUnit: cung cấp các phương thức chuyển đổi thời gian(các phương thức đều có kiểu dữ liệu trả về là long)

Eg: long millisec = TimeUnit.MINUTES.toMillis(minute);

![Exported image](Exported%20image%2020240225113137-3.png)  

//Date() : là một class đầu tiên dùng để mô tả ngày tháng trong java, hầu hết các phương thức đã lời thời, có hai constructor có thể sử dụng được:

![Exported image](Exported%20image%2020240225113137-4.png)

Một số phương thức thường được sử dụng:

![Exported image](Exported%20image%2020240225113137-5.png)

Ngoài ra còn có getHours(), getMonth(), getDate()…

  

// Calendar: là một abstract class(nên không thể khởi tạo), chứa thông tin của 3 bộ lịch gregorian calendar, buddhist calendar, japanese imperial calendar.

![Exported image](Exported%20image%2020240225113137-6.png)

Các phương thức để set, roll thời gian tùy ý:

![Exported image](Exported%20image%2020240225113137-7.png)

(*) Lưu ý: khi roll thì tùy vào field truyền vào mà các thông số thời gian sẽ roll như thế nào(có thể quay lại từ đầu).

Add thì sẽ roll chính xác thời gian theo logic với bất kì amount truyền vào (kể cả âm, dương, 0)

  

//DateFormat(): là một abstract class, giúp định dạng và phân tích ngày tháng, chuyển đổi từ String->date và ngược lại

![Exported image](Exported%20image%2020240225113137-8.png)  
![Exported image](Exported%20image%2020240225113137-9.png)  
  

//DATE TIME IN JAVA 8

![Exported image](Exported%20image%2020240225113137-10.png)  
![Exported image](Exported%20image%2020240225113137-11.png)  

/* LocalDate, LocalTime, LocalDateTime là 3 class phổ biến nhất cho việc sử dụng ngày giờ, không bắt buộc phải chỉ định rõ ràng múi giờ */

//LocalDate: biểu diễn một ngày theo định dạng ISO (yyyy-MM-dd), không chứa thông tin về giờ

Cú pháp: LocalDate localDate = LocalDate.now();

![Exported image](Exported%20image%2020240225113137-12.png)  
![Exported image](Exported%20image%2020240225113137-13.png)  
![Exported image](Exported%20image%2020240225113137-14.png)  

//LocalTime: thời điểm(giờ) theo định dạng ISO (hh:mm:ss.SSS), không chứa thông tin về ngày

Cú pháp: LocalTime localDate = LocalTime.now()

  
![Exported image](Exported%20image%2020240225113137-15.png)  
![Exported image](Exported%20image%2020240225113137-16.png)  
![Exported image](Exported%20image%2020240225113137-17.png)  

//LocalDateTime: biểu diễn cả ngày và giờ

Cú pháp: LocalDateTime now = LocalDateTime.now();

  
![Exported image](Exported%20image%2020240225113137-18.png)  
![Exported image](Exported%20image%2020240225113137-19.png)  
  
  

//Period: tính toán khoảng thời gian và trả về năm/tháng/ngày giữa hai mốc

Cú pháp: Period period =Period.between(firstDate, second Date);

![Exported image](Exported%20image%2020240225113137-20.png)  
![Exported image](Exported%20image%2020240225113137-21.png)  

//Duration: tính khoảng thời gian và trả về ngày /giờ/ phút / giây giữa hai mốc thời gian(nano sec)

Cú pháp: Duration duration = Duration.between(firstTime, secondTime);

![Exported image](Exported%20image%2020240225113137-22.png)  
![Exported image](Exported%20image%2020240225113137-23.png)