---
title: "Blog 3"
date: 2026-29-07
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# TỐI ƯU CHI PHÍ EC2 VỚI AWS COMPUTE OPTIMIZER RIGHT SIZING

*Rightsizing — điều chỉnh instance type và kích thước sao cho khớp với nhu cầu tài nguyên thực tế — là một trong những cách hiệu quả nhất để cải thiện ROI cho khoản đầu tư EC2. Nhưng thực hiện thủ công trên hàng trăm, hàng nghìn instance vừa tốn thời gian vừa dễ sai sót. AWS Compute Optimizer giải quyết bài toán này bằng cách phân tích cấu hình và mức sử dụng tài nguyên để đưa ra khuyến nghị rightsizing dựa trên dữ liệu.*

### 1. Bài toán vận hành
Phần lớn tổ chức không có cái nhìn rõ ràng về tỷ lệ hiệu năng-chi phí tối ưu cho instance của mình, dẫn đến hai thái cực:
* **Over-provisioning:** Gây lãng phí chi phí không cần thiết.
* **Under-provisioning:** Gây rủi ro suy giảm hiệu năng ứng dụng.

AWS Compute Optimizer phân tích lên đến 93 ngày dữ liệu sử dụng từ CloudWatch và tự động phân loại instance thành 4 nhóm: **Over-provisioned** (có thể downsize), **Under-provisioned** (cần upsize), **Optimized** (đã phù hợp) và **Idle** (nên terminate hoặc gộp lại).

### 2. Các chỉ số được phân tích
Compute Optimizer đánh giá dựa trên:
* CPU utilization
* Memory utilization (khi được bật CloudWatch Agent)
* Network I/O
* Disk I/O & EBS throughput/IOPS
* GPU utilization (nếu có)

Với mỗi trường hợp, hệ thống đề xuất tối đa 3 lựa chọn thay thế, xếp hạng theo mức tiết kiệm ước tính, rủi ro hiệu năng và mức độ nỗ lực di chuyển (migration effort) từ *Very low* đến *High*.

### 3. 5 Best Practice đáng chú ý
1. **Bật Cost Optimization Hub:** Tự động chuyển sang chế độ `AfterDiscounts`, tính đến các cam kết Savings Plans hoặc Reserved Instances hiện có để ước tính chi phí tiết kiệm chính xác thực tế.
2. **Bật Memory Metrics:** Bổ sung thu thập RAM qua CloudWatch Agent hoặc tích hợp bên thứ ba (Datadog, Dynatrace, Instana, New Relic) giúp khuyến nghị chính xác cho workload nặng về bộ nhớ.
3. **Tùy chỉnh Preference theo chiến lược riêng:** Điều chỉnh ngưỡng CPU utilization (P90/P95/P99.5), headroom cho CPU/memory, lookback period (14/32/93 ngày) ở cấp tổ chức, tài khoản hoặc khu vực.
4. **Đánh giá kỹ khuyến nghị Graviton:** Chuyển sang chip Graviton (ARM64) giúp cải thiện tới 40% tỷ lệ giá/hiệu năng, nhưng cần test khả năng tương thích kiến trúc và dependency trên staging trước khi áp dụng cho production.
5. **Xây dựng quy trình Rightsizing bài bản:** Thiết lập chu kỳ review định kỳ, ưu tiên instance tiết kiệm cao - rủi ro thấp, xác nhận với chủ sở hữu ứng dụng và theo dõi kết quả qua Cost Explorer (có thể tự động hóa qua Step Functions, EventBridge, Lambda).

### 4. Kết luận
AWS Compute Optimizer cung cấp nền tảng dữ liệu vững chắc để ra quyết định rightsizing một cách khoa học. Việc kết hợp đầy đủ chỉ số, tùy chỉnh preference và áp dụng quy trình review có hệ thống sẽ giúp doanh nghiệp tối ưu chi phí hạ tầng EC2 đáng kể mà vẫn đảm bảo hiệu năng.

---

### Hình ảnh & Minh họa
<div align="center">

![EC2 Rightsizing](/images/3-BlogsPosted/3.3-Blog3/right-sizing.png)

<p style="font-size: 1.15rem; font-weight: 600; margin-top: 8px;">
<i>Hình 1: EC2 Rightsizing</i></br>
<i>Nguồn: <a target="_blank" href="https://blog.easecloud.io/cost-optimization/right-size-ec2-and-eks/">https://blog.easecloud.io/cost-optimization/right-size-ec2-and-eks/</a></i>
</p>

</div>

### Link bài viết & Tham khảo
* **Link bài viết gốc (AWS Blog):** [https://aws.amazon.com/blogs/compute/optimize-ec2-costs-with-aws-compute-optimizer-right-sizing/](https://aws.amazon.com/blogs/compute/optimize-ec2-costs-with-aws-compute-optimizer-right-sizing/)