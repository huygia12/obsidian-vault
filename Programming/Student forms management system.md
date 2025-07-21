## Các từ khóa tìm kiếm trên GitHub

1. **"Java OCR form field detection"**
2. **"Java OpenCV template matching form field"**
3. **"Java OCR empty fields detection"**
4. **"Tesseract form field extraction"**
5. **"Java PDF form field extraction OpenCV"**
6. **"OpenCV blank field detection"**
7. **"Template matching for form fields"**

## Tiền xử lý ảnh:
- 1 Pixel trong ảnh được biểu bằng 3 giá trị cho từng kênh màu.
- `Opencv` sẽ nạp ảnh nạp theo thứ tự các kênh màu là `BGR` (thay vì `RGB` - hệ màu phổ biến nhất).

```python
imageGray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

- Công thức chuyển đổi từ `BGR` sang `grayscale``:
	`Gray=0.299⋅B+0.587⋅G+0.114⋅R`  
- Mỗi pixel sẽ được tính toán lại để chuyển sang mức xám.

```python
orb = cv2.ORB_create(maxFeatures)
(kpsA, descsA) = orb.detectAndCompute(imageGray, None)
```

- `kpsA` có dạng:
```json
{ 
	 "pt": kp.pt, # Tọa độ (x, y) 
	 "size": kp.size, # Kích thước 
	 "angle": kp.angle, # Góc 
	 "response": kp.response, # Độ phản hồi 
	 "octave": kp.octave, # Bậc (octave) 
	 "class_id": kp.class_id # ID lớp 
}
```

- Thuật toán `ORB` (`Oriented Fast and Rotated Brief`)
	- Phát hiện điểm đặc trưng (`Keypoint detection`) bằng thuật toán `FAST` (``Features from Accelerated Segment Test`): 
		- Dựa trên sự quan sát rằng một điểm góc thường có sự thay đổi mạnh mẽ về cường độ sáng ở nhiều hướng xung quanh nó.
		- Điểm góc P(pixel trung tâm) được xác định bằng cách xét hình tròn gồm 16 pixel xung quanh, nếu N pixel liên tiếp có giá trị sáng hơn hoặc tối hơn P một ngưỡng.
		- Để nhanh hơn nữa, FAST kiểm tra trước các pixel tại 4 điểm 12,3,6,9 giờ để xem ít nhất 3 trong số chúng có cùng cường độ sáng với điểm trung tâm P hay không. Nếu có thì loại luôn, nếu không thì xét tiếp đến 16 pixel còn lại nếu N điểm liên tiếp trên đường tròn có cường độ sáng khác với P thì được tính là 1 điểm góc. Trong ORB thì N = 9.
			![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR6QmN-NtqVABjgOBMOysecUBYPILDkmhlJkQ&s)
	- Tính toán hướng chủ đạo của điểm góc bằng phương pháp `Intensity Centroid` để khiến điểm góc trở lên bất biến với góc quay.
	- Tạo mô tả đặc trưng (`Descriptor`) bằng phương pháp `BRIEF` chứa thông tin về **quan hệ cường độ** giữa các pixel trong 1 vùng lân cận của điểm đặc trưng dưới dạng 1 chuỗi bit nhị phân, phục vụ cho việc so khớp hình ảnh nhanh hơn.

```python
method = cv2.DESCRIPTOR_MATCHER_BRUTEFORCE_HAMMING
matcher = cv2.DescriptorMatcher_create(method)
matches = matcher.match(descsA, descsB, None)
```

- Sử dụng phép đo khoảng cách `HAMMING` để so khớp thông tin trong mô tả đặc trưng giữa hai ảnh bằng phương pháp `bruteforce`, nếu hai descriptor có càng ít bit khác nhau thì chứng tỏ vùng lân cận của hai điểm đặc trưng này có mối quan hệ cường độ gần giống nhau. 

```python
(H, _) = cv2.findHomography(ptsA, ptsB, method=cv2.RANSAC)
(h, w) = template.shape[:2]
aligned = cv2.warpPerspective(image, H, (w, h))
```

- Tính toán ma trận chuyển đổi `3x3` giữa hai không gian ảnh (`homography`)  dựa trên các `keypoint` đã sàng lọc trước đó.

```python
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
dilated_img = cv2.dilate(gray_image, np.ones((7,7), np.uint8))
bg_img = cv2.medianBlur(dilated_img, 11)
diff_img = 255 - cv2.absdiff(gray_image, bg_img)
_, binary_image = cv2.threshold(diff_img, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)
```

- Dùng bộ lọc `dilate` để làm phình, giãn ảnh sau đó làm trung hòa phần mờ với bộ lọc `medianBlur`
## Trích xuất văn bản:
- Sử dụng mô hình `VGG-Transformer`: `VGG` sẽ giúp trích xuất các đzc trưng từ ảnh, còn `Transformer` sẽ giúp mô hình hiểu được mối quan hệ giữa các ký tự hoặc từ trong chuỗi văn bản để nhận diện chính xác hơn.

