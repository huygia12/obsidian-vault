---
created: 2024-02-26T12:41
updated: 2024-04-25T10:17
tags:
  - Java
  - Maven
---
## Concept :
- Là 1 Package Manager giống như npm hay Grandle.
- Đồng thời là 1 Build tool được ứng dụng trong việc build và deploy 1 Java Web Application.
- Plugin 
## `Pom.xml` :
- Maven hoạt động xoay quanh 1 Pom file (Project Object Model) là một file XML chứa tất cả nhưng thông tin của 1 project như tên, phiên bản, các Dependencies cần import trong project...
- POM file chỉ định cho Maven cần phải build những gì.
- Các bước hoạt động của Maven :
	1. Đọc file `pom.xml`
	2. Kiểm tra xem local Repository có các Dependency hay chưa. Nếu không có thì tải từ Central Repository hay Remote Repository.
	3. Thực thi các Maven Goal.
	4. Thực thi các plugins.

```XML
<modelVersion> : chỉ định ta đang sử dụng POM model có version nào.
<groupId> : là ID riêng biệt của tổ chức/cá nhân tạo ra project.
<artifactID> : là tên của project hiện tại.
<version> : chỉ định version của project. Theo convention thì SNAPSHOT là phiên bản đang được phát triển và RELEASE là phiên bản ổn định.
<packaging> : chỉ định khi build maven sẽ đóng gói project thành file được chỉ định như WAR hoặc JAR.
```

## Maven Build life cycle :
- Maven có 3 life cycle. Ngoài Clean, Site thì ta thường xét Default Life Cycle.  
- Quy trình Maven build 1 project được gọi là Default Life Cycle, được chia nhỏ thành phases :  ***Validate, Compile, Test, Package, Integration Test, Verify, Install, and Deploy***.
>![[Pasted image 20240309193859.png]]

- Mỗi Phase được map đến Goals (là method tương ứng nằm trong Plugin).
- Gọi 1 Phase ở sau đồng nghĩa với việc thực thi toàn bộ các Phase trước nó, đó là lý do tại sao lại dùng Phase mà không gọi trực tiếp Goals.
>![[Pasted image 20240309201935.png|300]]

- Chúng ta chỉ định Maven build project như thế nào thông qua câu lệnh : `mvn`

## Maven commands :
- Cú pháp : `mvn <phase name>`
	- Install the packages(dependencies) into the local repository : `mvn install`
	- Build project với maven (Tạo các file JAR hoặc WAR) : `mvn package`
	- Deploy to tomcat : `mvn tomcat:deploy`
	- Chạy unit test : `mvn test`
	- Clean project (Xoá bỏ các file, folder được tạo trong quá trình Maven Build) : `mvn clean`
	- Compile source code of the project : `mvn compile`
	- Run project : `java -jar [file.dot_jar]`

## MVNW:
- Để chạy ứng dụng maven không cần cài package mvn riêng trên mỗi máy, ta cần setup mvnw trong project:
	- Tạo folder **.mvn**: `mvn wrapper:wrapper`
	- Thêm file `mvnw` cho máy linux, hoặc `mvnw.cmd` cho máy window.

## Maven workflow :
- Khi chạy các câu lệnh ở bên trên, ta đang chạy các Phase trong Maven.
>![[Pasted image 20240302234419.png|450]]