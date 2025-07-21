## Nội dung liên quan:
[Message queue - `geeksforgeeks`](https://www.geeksforgeeks.org/message-queues-system-design/)
- Loose coupling: thay vì các service phụ thuộc vào nhau, nó phụ thuộc vào mỗi queue.
- Reliability: message được lưu trong queue, kể cả khi 1 service xử lý message bị down, khi nào nó được up lên thì sẽ lại xử lý như bình thường (giảm thiểu tối đa việc mất mát dữ liệu). 
- Scalability: tạo thêm các instance của queue (servers) để có thể xử lý lượng message lớn hơn khi cần thiết.

[RabbitMQ - `200lab`](https://200lab.io/blog/rabbitmq-la-gi#rabbitmq-hoat-dong-nhu-nao?)
[Kafka - `FPTshop`](https://fptshop.com.vn/tin-tuc/danh-gia/tim-hieu-ve-kafka-180407)

## Kafka
#### Khái niệm cơ bản:
- Topic: 
	- là một `data stream` (tương tự như 1 bảng trong cơ sở dữ liệu), hỗ trợ mọi loại dữ liệu
	- được xác định bởi tên
	- một `kafka cluster` có thể có rất nhiều `topic`
- Partition:
	- một `topic` có thể có rất nhiều `partition`, được chọn để tạo số lượng từ đầu (10, 100, ...)
	- `message` trong mỗi `partition` được sắp xếp theo thứ tự `offset` (tăng dần từ 0, hiểu như id). Thứ tự và `offset` chỉ được đảm bảo trong cùng một `partition`(các partition không chia sẻ offset với nhau), không được đặt lại kể cả khi message ấy bị xóa
	- `message` không thể thay đổi (cập nhật hoặc xóa) một khi đã ghi vào `partition`
	- `message` được giữ trong 1 khoảng thời gian có thể config được, mặc định là 1 tuần
- Producer:	
	- đưa dữ liệu vào `topic` với `producer serialization`
	- `message` được ghi theo `round-robin` vào `partition` nếu `key=null`	
	- có những lựa chọn sau cho việc nhận lại `acknowledgment`"
		- `acks`=0:  `producer` không đợi nhận lại `ack`
		- `acks`=1:  `producer` đợi nhận lại `ack` của `leader`
		- `acks`=all (hoặc -1):  `producer` đợi nhận lại `ack` của cả `leader` và `ISR`
			- `min.insync.replicas`: chỉ có thể <= `replication factor`, chỉ định cần bao nhiêu `ISR` (bao gồm cả leader) phải trả về `ack`, điều này đồng nghĩa với việc sẽ có thể chịu được `replication factor` - `min.insync.replicas` server sập.
- Message:
	![](Pasted%20image%2020250224174433.png)
- Partitioner:
	- quyết định `partition` nào mà `message` sẽ được ghi vào, sử dụng `key-hashing` để có thể map key vào `partition`
	- sử dụng thuật toán `murmur2` theo công thức
	``` javascript
	targetPartition = Math.abs(Utils.murmur2(keyBytes)) % (numPartitions - 1)
	```
	- StickyPartitioner:
		- Đây là đối tượng mặc định được set cho `partitioner` trong java
		- Nếu message được gửi đi cực nhanh (`linger.ms`) và nhỏ hơn một kích thước định trước (`batch.size`) thì kafka sẽ gom chúng lại và gửi thành 1 batch vào đúng 1 partition
		
- Consumer:
	- đọc dữ liệu từ `topic` sử dụng `consumer deserialization`, hoạt động theo kiểu `pull`
	- `message` được đọc từ theo `offset` từ thấp lên cao theo thứ tự được đảm bảo trong mỗi `partition` 
	- `message` được đọc theo từng `consumer group`, trong đó các `consumer` sẽ đọc từ các `partition` không trùng với nhau (mỗi consumer group có thể hiểu như là 1 service khác nên kể giữa các consumer group đọc trùng partition cũng không sao hết)  	
	- `kafka broker` sẽ tạo và lưu trữ các `consumer offset` trong topic `__consumer_offsets`, để xác định `consumer group` đã đọc đến đâu. Có thể theo một trong 3 chiến lược commit offset như sau:
		-  `at least once`: commit sau khi đã đọc và xử lý thành công `message`, điều này có thể dẫn đến việc đọc lại nhiều lần nếu quá trình xử lý fail (cần có cơ chế đảm bảo việc đọc lại không ảnh hưởng đến logic)
		-  `at most once`: commit sau khi đọc xong và trước khi xử lý, nếu đọc thất bại dữ liệu sẽ bị mất
		-  `exactly once`:
- Broker(bootstrap server):
	- một `cluster` có thể bao gồm nhiều `brokers` (servers), mỗi `broker` được xác định bởi id là một int
	- `message` của `topic` có thể trải dài giữa nhiều `broker`, không phải broker nào cũng cần có tất cả các loại topic như những `broker` khác trong `cluster`
	- chỉ cần biết 1 `broker` là có thể biết hết tất cả các `broker` còn lại trong `cluster`
	![](Pasted%20image%2020250225164301.png)
- Topic replication factor:
	- một topic nên có `replication factor` > 1 (thường là 2 hoặc 3), khái quát thì nếu `replication factor` = n thì topic có thể chịu tối đa n-1 broker loss
	- bất kì lúc nào, một trong số `broker` sẽ chứa `leader` của `partition` và những `broker` còn lại có thể chứa các `ISR`(in sync replica - bản sao được đồng bộ cực nhanh)
	- `producer` chỉ có thể gửi dữ liệu vào `leader` của `partition` đó
	- `customer` mặc định đọc dữ liệu từ `leader` của `partition` đó, từ phiên bản 2.4 của kafka thì consumer có thể đọc từ replica gần nhất (giảm độ trễ, giảm network cost nếu dùng cloud)
	![](Pasted%20image%2020250225164847.png)
- Zookeeper:
	- quản lý các `broker`(dưới dạng danh sách), số lẻ lần (không quá 7)
	- giúp chọn ra `leader` trong `partitions`
	- gửi thông báo cho kafka nếu có thay đổi (topic mới, broker chết, broker hồi phục, xóa topic, ...)
	- kafka 2.x không thể hoạt động nếu không có `zookeeper`, từ 3.x trở đi được thay thế bằng `kafka raft`
	- không chứa `consumer offset` từ 0.10 trở đi
	![](Pasted%20image%2020250225173833.png)
- `Partition rebalance`:
	- Xảy ra khi consumer rời hoặc join vào một group, hoặc một partition mới được thêm vào topic.
	- `Eager rebalance`: tất cả consumer dừng, bỏ hết partitions mà nó được phân phối, rejoin lại group và được phân mới partitions (có thể không còn là partitions như cũ nữa). Vậy nên trong một khoảng thời gian ngắn group sẽ ngưng hoạt động (stop-the-world). Có 3 strategy:
		- `RangeAssignor`
		- `RoundRobin`
		- `StickyAssignor`
	- `Cooperative rebalance (incremental rebalence)`: Chỉ phân phối lại một phần nhỏ partitions từ consumer này tới consumer khác, cho nên những consumers không bị tái phân phối sẽ hoạt động bình thương.
		- `CooperativeStickyAssignor`
- `Static group membership`: nếu đặt `group.instance.id` sẽ khiến cho một consumer thành một static group member. Khi consumer đó rời group không quá `session.timeout.ms` thì việc phân phối lại partitions sẽ không diễn ra và được giữ nguyên cho consumer đó.
#### Commands:
###### Getting started:
- Start zookeeper
```bash
zookeeper-server-start.sh <path-to-zookeeper.properties>
```
- Start kafka server
```bash
kafka-server-start.sh <path-to-server.properties>
```
###### Topic:
- List topic
```bash
kafka-topics.sh --bootstrap-server localhost:9092 --list
```
- Create topic
	- `_` và `.` được xét giống nhau nên không được đặt tên của 2 topic chỉ khác nhau mỗi hai ký tự này
	- default partitions = 1 (khi không thêm tham số `--partitions`)
	- default replication factor  = 1 (khi không thêm tham số `--replication-factor`) và không được lớn ơn số lượng broker
```bash
kafka-topics.sh --bootstrap-server localhost:9092 --create --topic <topic-name> --partitions <partition-number> --replication-factor <replication-number>
```
- Describe topic
	- default hiển thị hết các topic (khi không thêm tham số `--topic`)
```bash
kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic <topic-name>
```
- Delete topic
```bash
kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic <topic-name>
```
###### Provider:
- Producing 
	- với properties (khi thêm tham số `--producer-property`): `acks = all`, `acks = 0`, `acks = 1`
	- default tự động tạo topic (khi không tồn tại)
	- sử dụng key cho từng message (thêm `--property parse.key=true`), xác định key và content ngăn cách nhau (thêm tham số) `--property key.separator=<symbol>`)
```bash
kafka-console-producer.sh --bootstrap-server localhost:9092 --topic <topic-name> --producer-property <property> --property parse.key=true --property key.separator=<seprator-symbol>
```
###### Consumer:
- Consuming 
	- default sẽ được message theo thời gian thực
	- đọc từ đầu (khi thêm tham số `--from-beginning`)
	- hiển thị thêm các thuộc tính của message (thêm `--property print.<property-name>=true`)
	- tham gia vào 1 group (khi thêm tham số `--group <group-name>`)
```bash
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic-name> --from-beginning --formatter kafka.tools.DefaultMessageFormatter --property print.timestamp=true --property print.key=true --property print.value=true --group my-first-group

```
###### Consumer group:
- Xem chi tiết 1 group:
	- lag: số message chưa được consume
```bash
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group <group-name>
```
- Liệt kê group:
```bash
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
```
- Reset lại `consumer-offset`
	- reset lại tất cả topic (thêm option `--all-topics`)
	- reset lại 1 topic cụ thể (thêm option `--topic <topic-name>`)
	- forward offset by n (thêm option `--shift-by <integer>`)
	- backward offset by n (thêm option `--shift-by <negative-integer>`)
```bash
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group <group-name> --reset-offsets --to-earliest --execute --topic <topic-name>
```


> [!warning] Lưu ý khi lập trình với Java:
>#### **Tại sao phải sử dụng producer.flush() ?**
> - Producer khi thực hiện send một record đi thì thực chất sẽ gửi nó đến một Buffer được quản lý bởi  thread Kafka producer (từ lúc tạo producer) riêng để xử lý gửi record. Các record không được gửi ngay lập tức mà được gom nhóm trong buffer. Kafka quyết định gửi dựa trên `batch.size` hoặc thời gian chờ `linger.ms`. Trước khi chương trình kết thúc, cần gọi `flush()` hoặc `close()` để đảm bảo tất cả dữ liệu được gửi đi.
>#### **Tại sao phải cần tới cơ chế heartbeat nữa ?**
> - Do khi polling, nếu cần phải xử lý lượng dữ liệu lớn thì việc gọi tới broker trước khi nó cho rằng consumer đã ngắt kết nối có thể gián đoạn. Do đó cần thêm cơ chế heartbear chạy độc lập trong một thread hoàn toàn riêng biệt.
>#### **Producer safe settings **
> - Mặc định tại version >= 3.x nhưng phải tự set nếu ở version nhỏ hơn
> - `acks`: all
> - `min.insync.replicas`: 2
> - `enable.idempotance`: true
> - `retries`: MAX_INT
> - `delivery.timeout.ms`: 120000
> - `max.in.flight.request.per.connection`: 5




#### Tổng quan:
![](Pasted%20image%2020250227211338.png)
	
![](Pasted%20image%2020250227211440.png)