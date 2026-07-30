---
title: "Blog 1"
date: 2026-29-07
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
includeInReport: false
---

# AMAZON BEDROCK & NOVA PRO: PHÂN TÍCH SỰ CỐ VẬN HÀNH BẰNG AI ĐA PHƯƠNG THỨC

*Khi một ứng dụng cloud-native gặp sự cố, đội ngũ vận hành thường phải rà soát hàng loạt nguồn dữ liệu quan sát (observability) khác nhau trong áp lực khôi phục dịch vụ càng nhanh càng tốt. Bài viết giới thiệu cách kết hợp Amazon Bedrock và Amazon Nova Pro để xây dựng hệ thống phân tích sự cố tự động, có khả năng xử lý đồng thời cả dữ liệu văn bản lẫn hình ảnh.*

### 1. Bài toán vận hành
Các công cụ giám sát truyền thống chỉ dừng lại ở việc cảnh báo khi sự cố xảy ra, còn việc phân tích và tương quan dữ liệu phức tạp vẫn phải dựa vào con người. Quá trình này vốn tốn nhiều thời gian và dễ sai sót, khiến thời gian downtime kéo dài và ảnh hưởng đến trải nghiệm khách hàng. Bài toán đặt ra là làm sao tự động hóa được bước phân tích này mà không đòi hỏi đội ngũ vận hành phải có chuyên môn sâu về machine learning hay data science.

### 2. Cơ chế hoạt động
**Luồng xử lý:**  
`Nguồn dữ liệu quan sát (CloudWatch, Config, X-Ray, sơ đồ kiến trúc) → Thu thập & lưu trữ (Amazon S3) → Phân tích đa phương thức (Amazon Bedrock + Nova Pro) → Insight & đề xuất khắc phục`

Hệ thống vận hành theo bốn giai đoạn chính:
* **Thu thập dữ liệu:** Dữ liệu được thu thập và tương quan từ nhiều nguồn hạ tầng khác nhau: chỉ số từ Amazon CloudWatch, lịch sử thay đổi cấu hình từ AWS Config, và các dấu vết request (traces) từ AWS X-Ray. Khi sự cố xảy ra, script thu thập dữ liệu sẽ chụp lại toàn bộ thông tin liên quan trong khoảng thời gian xảy ra outage và lưu vào Amazon S3.
* **Phân tích đa phương thức:** Script gọi đến Amazon Bedrock với model Amazon Nova Pro — mô hình có khả năng xử lý đa phương thức (multimodal), tức đọc hiểu được cả dữ liệu văn bản (log, metric) lẫn dữ liệu hình ảnh (sơ đồ kiến trúc hệ thống) trong cùng một lần suy luận. Nhờ vậy, mô hình không chỉ phân tích số liệu thô mà còn "nhìn" được cấu trúc hệ thống để hiểu bối cảnh sự cố sâu hơn.
* **Đề xuất khắc phục:** Kết quả đầu ra là một bộ insight toàn diện: danh sách các nguyên nhân khả nghi được xếp hạng theo xác suất, các bước xử lý sự cố cụ thể, và nội dung thông báo gợi ý để gửi đến khách hàng — giúp đội vận hành nhanh chóng áp dụng bản sửa lỗi và rút ngắn đáng kể Mean Time to Resolution (MTTR).

### 3. Quy trình triển khai thực nghiệm
Để minh họa cụ thể, bài viết sử dụng PetShop làm ví dụ:
1. Thiết lập Amazon S3 bucket để lưu dữ liệu quan sát và sơ đồ kiến trúc ứng dụng.
2. Giả lập sự cố bằng cách thay đổi rule của security group trên load balancer để chặn traffic HTTP.
3. Chạy script thu thập dữ liệu để lấy chỉ số CloudWatch, thay đổi cấu hình từ AWS Config và trace từ X-Ray, tải toàn bộ lên S3.
4. Chạy script phân tích gọi Amazon Bedrock với Nova Pro để xử lý dữ liệu đa phương thức và xuất ra khuyến nghị khắc phục.

### 4. Kết luận
Việc kết hợp các dịch vụ observability của AWS với generative AI mở ra một hướng tiếp cận mới cho công tác phản ứng sự cố: tự động hóa bước phân tích dữ liệu đa chiều vốn tốn nhiều thời gian nhất, đồng thời nâng cao chất lượng giao tiếp với khách hàng trong quá trình xử lý sự cố. Đây không chỉ là giải pháp cho các thách thức vận hành hiện tại, mà còn có khả năng mở rộng để đáp ứng độ phức tạp ngày càng tăng của hạ tầng cloud hiện đại.

---

### Hình ảnh & Minh họa
<div align="center">

![Sơ đồ kiến trúc xử lý sự cố đa phương thức bằng Amazon Bedrock](/images/3-BlogsPosted/3.1-Blog1/solution_architecture.jpg)

<p style="font-size: 1.15rem; font-weight: 600; margin-top: 8px;">
<i>Hình 1: Sơ đồ mô tả quy trình xử lý sự cố đa phương thức bằng Amazon Bedrock</i>
</p>

</div>

### Link bài viết & Tham khảo
* **Link bài viết gốc (AWS Blog):** [https://aws.amazon.com/blogs/mt/using-amazon-bedrock-and-amazon-nova-for-ai-powered-incident-response/](https://aws.amazon.com/blogs/mt/using-amazon-bedrock-and-amazon-nova-for-ai-powered-incident-response/)