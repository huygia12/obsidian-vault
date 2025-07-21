---
created: 2024-02-25T11:31
updated: 2023-07-24T10:05
---
- **Csv:** **(hoạt động tương tự exel)**
- Lưu trữ dữ liệu theo từng cột
- Phân chia các trường của dữ liệu bằng dấu ","
- Ghi vào file .csv
- Đọc từ file .csv

![Exported image](Exported%20image%2020240225113121-0.png) ![Exported image](Exported%20image%2020240225113121-1.png)  

- **Thư viện open.csv: Thao tác với csvToBean và statefullBeanToCsv**
- Đọc 1 file với CsvToBeanBuilder<>()
- Trong quá trình tạo class, mỗi thuộc tính cần chỉ ra vị trí của cột thuộc tính trong file csv: sử dụng Annotation(có nhiều loại annotation khác nữa)
- Write 1 file với statefullBeanToCsv()
- Áp dụng thêm các hàm with… để thêm các option lúc đọc, ghi file:

+ withQuoteChar(CSVWriter.DEFAULT_QUOTE_CHAR): "

+ withQuoteChar("ki_tu"): ky_tu

+ withSeparator(CSVWriter.DEFAULT_SEPARATOR): ,

+ withSeparator("ky_tu"): ky_tu

+ withSkipLine(so_dong): bỏ qua số dòng lúc đọc(viết)

+ withMappingStrategy: ??????

![Exported image](Exported%20image%2020240225113121-2.png) ![Exported image](Exported%20image%2020240225113121-3.png) ![Exported image](Exported%20image%2020240225113121-4.png)