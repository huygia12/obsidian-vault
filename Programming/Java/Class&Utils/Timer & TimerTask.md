---
created: 2024-02-25T11:31
updated: 2024-03-06T20:51
tags:
  - JavaClass
  - JavaThread
---
## Concept : 
- Hai class trong package *java.util* được sử dụng để lên lịch cho một công việc và chạy nó trong Background với 1 Thread. 
- `TimerTask` là công việc cần thực thi và `Timer` là lịch trình được thực thi.

## Work flow : 

- **Task** : Tạo Task bằng cách kế thừa class `TimerTask`.
```Java
public class MyTask extends TimerTask {
	@Override
	public void run(){
		System.out.println("RUn my Task  " + new Date());
	}
}
```

- **Timer**: Lên lịch cho task được tạo với method schedule() với các đối số:
	- Delay : sau bao lâu thì chạy.
	- Task : Công việc được thực thi.
	- Time(Date) : chỉ định bao giờ thì được phép thực thi.
	- Period : chu kỳ được lặp lại.
```Java
public class DemoTaskOnce{
	public statuc void main(String[] args){
		MyTask myTask = new MyTask();
		Timer timer = new Timer();
		System.out.println("Curretn time: " + new Date());
		timer.schedule(myTask, 5000);	
	}
}
```
  
