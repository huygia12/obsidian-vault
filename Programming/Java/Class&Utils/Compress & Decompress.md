---
created: 2024-02-25T11:31
updated: 2023-07-24T23:36
---
- **N****én****&Giải Nén biến dữ li****ệu** **sử dụng Deflater & Inflater :**
- Nằm trong package util.zip
- Inflater: Giải nén
- Deflater: nén dữ liệu
![Exported image](Exported%20image%2020240225113118-0.png)

getBytes => setInput => end

getBytes => setInput => finish

  

- **Nén File&Giải nén File sử dụng DeflaterStream & InflaterStream :**
- Không thể thực hiện giải nén bằng winrar hay công cụ hỗ trợ nào khác ngoài code tay.
- Nén : DeflaterInputStream(nén dữ liệu ở đầu vào) && DeflaterOutputStream(nén dữ liệu ở đầu ra).
![Exported image](Exported%20image%2020240225113118-1.png)  

**// DeflaterInputStream: InputStream => DeflaterInputStream => OutputStream**

![Exported image](Exported%20image%2020240225113118-2.png)

**// DeflaterOutputStream**

![Exported image](Exported%20image%2020240225113118-3.png)  
- Giải nén: InflaterInputStream(giải nén ở đầu vào) && InflaterOutputStream(giải nén ở đầu ra).

**// InflaterInputStream**

![Exported image](Exported%20image%2020240225113118-4.png)

**// InflaterOutputStream**

![Exported image](Exported%20image%2020240225113118-5.png)  
- **Nén File&Giải nén File sử dụng ZipStream :**
- Mỗi Object ZipInput/ZipOutput đều các method nén và giải nén
- Nén : OutputStream => ZipOutputStream => InputStream => putNextEntry(tạo new Entry) => write( byte[] ) => close
![Exported image](Exported%20image%2020240225113118-6.png)- Giải nén : InputStream => InputZipStream => getNextEntry => OutputStream => write(bytes[]) => close
- ![Exported image](Exported%20image%2020240225113118-7.png)
  
- **Lưu ý khi sử dụng giải thuật nén:**
- Dữ liệu sau khi nén sẽ bao gồm:

+ Thông tin nén : được sử dụng để khi giải nén dữ liệu, có chiếm một khoảng data nhất định.

+ Chứa dữ liệu nén : dữ liệu nhỏ thì không nên nén vì sau khi nén dữ liệu sẽ lớn hơn ban đầu.