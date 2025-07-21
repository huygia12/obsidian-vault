---
created: 2024-03-01T08:02
updated: 2024-03-05T07:12
tags:
  - English
  - Technical
---
## New word :
[[English_Dictionary#^41291a|Carry out]]


---
# Discussion :
1. What is a network?
2. What network devices do you know?
3. How many common types of networks do you know? what are they?
4. What do you know about them?
5. What do LAN, WAN, MAN, PAN, stand for?
6. What is a network topology?
	- Is the arrangement of the various elements (links, nodes, etc...) of a computer network.
		- A node is either a connection point, a redistribution point, or a communication endpoint.
		- A data link is the means of connecting one  location to another for the purpose of transmitting and receiving digital information.

7. How many types of network topologies do you know? what are they?
	- In the bus topology, each node connected to a single cable, by the help of interface connectors. This central cable is the backbone of the network and is known as the bus.
	- In the star topology, each network host is connected to a central hub with a point-to-point connection. Every node is connected to a central node called hub, router or switch.
	- In a ring topology, there is no server computer present; all nodes work as a server and repeat the signal.
		-  The disadvantage of this topology is that if one node stops working, the entire network is affected or stops working.
		
8. Which network topologies are common ?

---
## Home work :
1. What are the advantages and disadvantages of bus, star, ring topology?
	- Star:
		- Advantages : it is very reliable - if one goes down, all the others will still work. No disruptions to the network when connecting or removing devices.  
		- Disadvantages : The remote devices are unable to communicate directly. Instead, they must communicate via the central computer only. Additionally, the star network is very susceptible to failure if the central goes down.
	- Bus :
		- Advantages : It's the easiest network topology for linearly connecting peripherals or computers. It's easy to remove or add devices in the network without affecting any other devices.
		- Disadvantages : Bus topology is not good for large networks. Identification of problems becomes difficult if the whole network goes down.
	- Ring :
		- Advantages : Additional computers can be added after without impacting performance of the network. All the computers accesses to the resources equally. It also cheap to install and expand.
		- Disadvantages : Due to the uni-directional Ring, a data must pass through all the nodes in the way to another node. In order to pass data in the topology, all the nodes must be turned on.

2. Task 5 (P.108).
	1. Protocols
	2. Distinction
	3. Distributed systems
	4. LANs
	5. screen handling
	6. Queries
	7. Parses
	8. Workstations
	9. Synchronous
	10. fibre-optic
	11. Environments

3. Translate Task 11 (P.110)
	1.  Mô hình sao :
		Trong cấu hình sao, máy tính trung tâm thực hiện tất cả các tiến trình và điều khiển các chức năng. Tất cả thiết bị truy cập được kết nối trực tiếp tới máy tính trung tâm. Cấu hình dạng sao có hai giới hạn chính. Đầu tiên, những thiết bị từ xa không thể liên lạc trực tiếp. Thay vào đó, chúng phải liên lạc thông qua máy tính trung tâm. Thứ hai, mạng hình sao rất dễ bị sụp đổ, kể cả trên máy tính trung tâm hay các liên kết truyền tải.
	2. Mô hình chuyển đổi :
		Bộ chuyển đổi trung tâm, có thể là 1 tổng đài điện thoại, được sử dụng để kết nối các thiết bị khác nhau trong mạng 1 cách trực tiếp. Một khi liên kết được thiết lập, hai thiết bị liên lạc như thể chúng được liên kết trực tiếp không cần sự can thiệp từ bất kể thiết bị nào. Ở cuối của phiên làm việc, kết nối bị đóng, giải phóng dung lượng cho những người dùng khác và cho phép truy cập tới các thiết bị khác. Có thể sử dụng nhiều bộ chuyển đổi để tạo các đường truyền thay thế.
	3. Mô hình vòng :
		Mỗi thiết bị được gán vào trong một mạng có dạng như 1 vòng lặp liên tục. Dữ liệu truyền theo duy nhất 1 hướng và theo 1 tốc độ duy nhất quanh vòng lặp.  Các thiết bị gửi thông tin chỉ khi chúng được kiểm soát bởi 'token'.  Token là 1 gói dữ liệu chỉ định thiết bị nào có quyền điều khiển. Thiết bị nhận thực hiện nhận token, sau đó xóa nó cho lần sử dụng khác một khi đã nhận được tin nhắn. Chỉ một thiết bị gửi dữ liệu ở bất kì thời điển nào, và mỗi thiết bị phải đang hoạt động để mạng lưới hoạt động được.
	4. Mô hình Bus/Ethernet:
		Một mạng bus bao gồm một đoạn dây kết thúc ở mỗi đầu thiết bị được kết nối tới. Trong 1 mạng dựa trên Bus, mỗi thiết bị có thể phát tin khi mà nó bị nhận thấy đã yên lặng trong 1 khoảng thời gian cố định. Tất cả nhưng thiết bị nhận tín hiệu phát và quyết định từ nội dung của tin nhắn rằng tin có dành cho chúng hay không. Vấn đề duy nhất xảy ra là khi hai thiết bị cố gắng gửi trong cùng 1 lúc. Khi 1 thiết bị gửi xác định được đường truyền của thiết bị khác, chúng sẽ tự hủy cái của chúng.

4.  Task 12 (P.112)
	1. What is Switched used for ?
	2. Does the Data go by multiple direction round the loop?
	3. Can any devices in the Ring topology send the data at any moment?
	4. In a bus-based network, how can devices determine message was intended for them?
	5. In the bus-based network, what does a sending device do whenever it detects another's transmission?

5. Task 13 (P.112)
	1. Ring
	2. Bus/Ethernet
	3. Star
	4. Switched
	5. Ring
	6. Star, Bus/Ethernet

6. Summarize reading 1 in Vietnamese.
		Lớp ứng dụng chuyển dữ liệu con người có thể đọc được sang các bit và gán chúng vào chúng 1 phần đầu để xác minh máy tính gửi và máy tính nhận. Lớp trình bày đảm bảo tin nhắn được truyền đi bằng ngôn ngữ mà máy tính nhận có thể thông dịch (thường là dạng ASCII), thêm 1 phần đầu khác chỉ định ngôn ngữ cung như đồ hình nén và mã hóa. Lớp phiên mở và giữ các liên lạc giữa các điểm trên mạng, quyết định xem tin nhắn được truyền theo kiểu bán song công hay song công, đồng thời thêm vào phần đầu của phiên. Lớp giao vận bảo vệ dữ liệu được gửi đi, sao lưu và chia nhỏ dữ liệu, rồi thêm tiếp vào phần mở đầu định dang của mỗi phần được chia và vị trí của chúng. Lớp mạng chọn đường đi cho tin nhắn, chia dữ liệu thành các gói, thêm vào phần đầu thứ tự gói và địa chỉ máy tính nhận. Lớp liên kết dữ liệu giám sát đườn truyền, đảm bảo gói được đi tới điểm tiếp theo thành công. Lớp vật lý mã hóa gói vào phương tiện để mang theo chúng theo. Mỗi trạm trung chuyển tính toán và xác thực gói, thực hiện điều tiết để ngăn chặn tắc nghẽn trên mạng. Nối cuối thực hiện nhận, xử lý theo chiều ngược lại bên gửi.

7. Exercise 1 (P.116)
	1. The transport layer subdivides the data into segments. The network layer subdivides the data into packets.
	2. Checksum tests can be used later to determine if the data was scrambled. 
	3. Data-link layer keeps a copy of each packet until it receives confirmation from the next point along the route that the packet has arrived undamaged.
	4. An Intermediate node calculates and verifies the checksum for each packet. It may also reroute the message to avoid congestion on the network.
	5. a. Presentation   b. Network   c. Physical   d. Data-Link   e. Application   f. Session   g. Network   
		h.Transport   i. Data-link   

8. Exercise 2 (P.117)
	a. T   b. F   c. F   d. T   e. F   f. T   g. T