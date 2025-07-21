---
created: 2024-02-25T11:31
updated: 2023-07-20T22:19
---
- Collections **vs** collection :

+ Collections: là một khuôn khổ cung cấp một kiến trúc(các phương thức static) để lưu trữ và thao tác tới nhóm các đối tượng: tím kiếm, phân loại, chèn, xóa,… có thể thực hiện bởi **java collections**.

+ Collection: là một root interface trong hệ thống cấp bậc Collection. **Java collection** cung cấp nhiều interface(Set, list, queue, deque) và các lớp (arraylist, vector, linkedlist, priorityqueue, hashset, linkedhashset, treeset, … ).

  
- Gói java.util chứa tất cả các lớp và interface của Collection
![Exported image](Exported%20image%2020240225113123-0.png)  
![Exported image](Exported%20image%2020240225113123-1.png)

  
- **Set:** ==là một collection không thể chứa 2 giá trị trùng lặp. Set được sử dụng để biểu diễn các bộ, chẳng hạn như bộ tú lu khơ, thời khóa biểu của học sinh, các tiến trình đang chạy trên máy tính…==
  
- **List:** ==là một interface có thứ tự (đôi khi còn được gọi là một chuỗi). List có thể chứa các phần tử trùng lặp. Thường có quyền kiểm soát chính xác vị trí các phần tử được chèn vào và có thể truy cập chúng bằng chỉ số (vị trí của chúng).==
  
- **Queue (hàng đợi):** ==là một collection được sử dụng để chứa nhiều phần tử trước khi xử lý. Bên cạnh các thao tác cơ bản của collection, Queue cung cấp các thao tác bổ sung như chèn, lấy ra và kiểm tra. Queue sử== ==dụng bằng cách lấy phần tử ra ở đầu và thêm phần từ vào từ cu====ối====. Một dạng class của queue là PriorityQueue được implement từ queue, hoạt động tương tự nhưng có thể ưu tiên một số phần tử được lấy ra tr====ước====, ưu tiên.==
  
- **Deque:** ==là một collection== ==kế thừa từ queue, m====ột Deque cung cấp các thao tác bổ sung như chèn, lấy ra và kiểm tra== ==từ cả hai phía====. Deques có thể được sử dụng như là FIFO (first-in, first-out - vào trước, ra trước) và LIFO (last-in, first-out - vào sau, ra trước). Trong một Deque, tất cả các phần tử mới có thể được chèn vào, lấy ra và lấy ra ở cả hai đầu.== ==Có hai dạng class của deque là linkedList và arrayDeque.==
  
- **Map:** ==là một đối tượng ánh xạ mỗi key tương úng với một giá trị. Map không thể chứa giá trị trùng lặp. Mỗi key có thể ánh xạ đến nhiều nhất một giá trị.==

  
  
  

==Hàm .keySet() : trả về toàn bộ key có trong collection implements Set.==

==Hàm .forEach() : để duyệt mảng==

  
  
  
  
  

- ==Collection== ==trong java là non-generic collection trước jdk1.5. Từ jdk 1.5 là generic(java 5). Nó cho phép chỉ có một kiểu đối tượng trong collection(an toàn hơn khi không cần phải ép kiểu tại runtime). Tham số hóa kiểu dữ liệu==

==EG: ArrayList<String> list = new ArayList<String>():==

  
- ==Có thể duyệt các phần tử trong Collection của java theo hai cách đó l====à====:==

==+ Stream(java 8):==

==Cú pháp: list.Stream().forEach(action);==

  
  

==//== ==Một số method thông dụng của Colletions:==

- **Collections.unmodifiableList(list)** ==: trả về một list các phần tử được== **tham chiếu** ==từ list làm tham số, nhưng list được trả về chỉ ở chế độ read-only(Không được thêm hay xóa phần tử trong list). Nếu bất kì nỗ lực để thay đổi nào kể cả trực tiếp hay gián tiếp đều sẽ dẫn đến :==
- **So sánh ArrayList và Vector**==: vector luôn có 10 ptu để không phải tốn tgian tạo và gán giá trị vào mảng mới như arrayList, mỗi khi vượt quá 10 ptu thì capacity lại increase lên 10 bằng cách gán vào một mảng mới, vì vậy vector xử lý có phần nhanh hơn arrayList.==

  

==+ Iterator interface:==

==Cú ph====áp====: Iterator it = list.Iterator();==

==While(it.hasNext()){====￼== ==action==

==}==

  
  

==Unsupported Operation Exception==