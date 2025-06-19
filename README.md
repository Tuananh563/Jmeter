

##  BÁO CÁO KIỂM THỬ HIỆU NĂNG WEBSITE BẰNG APACHE JMETER

**Tên dự án:** Kiểm thử hiệu năng website Simplilearn <br>
**Người thực hiện:** \Trần Mạnh Tuấn Anh <br>
**Ngày kiểm thử:** \19/6/2025 <br>
**Công cụ sử dụng:** Apache JMeter 5.6.3 <br>
**Trang web kiểm thử:** [https://www.simplilearn.com](https://www.simplilearn.com)



### 1. Mục tiêu kiểm thử

Đánh giá hiệu năng website thông qua khả năng phản hồi với nhiều người dùng truy cập đồng thời, bao gồm thời gian phản hồi trung bình, tốc độ xử lý, và tỷ lệ lỗi.



### 2. Cấu hình kiểm thử

* **Thread Group:**

  * Số lượng người dùng (Number of Threads): 5
  * Ramp-up period: 2 giây
  * Loop Count: 1

* **Sampler:** HTTP Request đến `https://www.simplilearn.com`

* **Listeners:**

  * View Results Tree
  * Summary Report
  * Aggregate Report



### 3. Kết quả kiểm thử (từ Aggregate Report)

| Thông số                          | Giá trị          |
| --------------------------------- | ---------------- |
| Số mẫu (Samples)                  | 5 yêu cầu        |
| Thời gian phản hồi trung bình     | 2324 ms          |
| Độ trễ trung vị (Median)          | 246 ms           |
| 90% Line                          | 369 ms           |
| 95% Line                          | 10540 ms         |
| Thời gian lớn nhất (Max)          | 10540 ms         |
| Thời gian nhỏ nhất (Min)          | 234 ms           |
| Tỷ lệ lỗi (Error %)               | 0.00%            |
| Throughput (tốc độ xử lý)         | 1.5 request/giây |
| Dung lượng nhận (Received KB/sec) | 14.54 KB/s       |
| Dung lượng gửi (Sent KB/sec)      | 0.01 KB/s        |

*Hình ảnh minh chứng:*
 * View Results Tree
![{F2527071-D7EE-4257-9560-DEB9EBC072A4}](https://github.com/user-attachments/assets/fe087a23-766a-49c5-9ceb-b7051c4b8a2e)

 * Summary Report
![{DA1D5076-BDF3-4D6F-9B66-F4FF9BB49A15}](https://github.com/user-attachments/assets/a636573b-ec95-4213-b7c9-ba3d32407f98)

 * Aggregate Report
![{FED364C3-8CD7-4906-8C82-6F040D471602}](https://github.com/user-attachments/assets/ca198838-f25a-4f2a-a597-8e4ec01e1cd3)




### 4. Đánh giá kết quả

* **Tỷ lệ lỗi bằng 0%**, cho thấy các yêu cầu đều thành công.
* **Thời gian phản hồi trung bình là 2.3 giây**, có thể chấp nhận được với tải nhẹ (5 users).
* **Độ lệch lớn giữa 90%, 95% và Max** (10540ms) cho thấy có ít nhất 1 request mất nhiều thời gian xử lý, cần kiểm tra thêm nguyên nhân (có thể do tốc độ mạng, cache, xử lý server...).
* Throughput đạt 1.5 request/giây là ổn định ở mức tải nhỏ.

---

### 5. Kết luận & Đề xuất

**Kết luận:**
Hệ thống hoạt động ổn định và có khả năng đáp ứng yêu cầu từ 5 người dùng đồng thời với tỷ lệ thành công 100%. Tuy nhiên, vẫn có hiện tượng một số request bị trễ, cần tiếp tục theo dõi khi tăng tải.

**Đề xuất:**

* Kiểm tra tốc độ mạng và giới hạn server phản hồi.
* Thực hiện thêm các bài kiểm thử với số lượng user lớn hơn (ví dụ 20, 50, 100...)
* So sánh hiệu năng với các thời điểm khác nhau trong ngày (giờ cao điểm vs giờ thấp điểm)

