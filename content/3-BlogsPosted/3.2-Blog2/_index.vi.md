---
title: "Blog 2"
date: 2026-29-07
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# XÂY DỰNG END-TO-END AGENTIC SRE VỚI AWS DEVOPS AGENT

*Với các hệ thống hiện đại gồm serverless function, microservice và kiến trúc hướng sự kiện, việc phản ứng sự cố ngày càng phức tạp: kỹ sư phải tự tương quan dữ liệu từ nhiều công cụ giám sát khác nhau trong khi chạy đua với SLA. AWS DevOps Agent hướng đến việc thay đổi hoàn toàn cách vận hành này — hoạt động như một tác nhân AI tự động, luôn túc trực, điều tra sự cố ngay khi xảy ra và hỗ trợ cả môi trường multi-cloud lẫn hybrid, không chỉ riêng AWS.*

### 1. Kiến trúc triển khai
Giải pháp được tổ chức trên ba tài khoản AWS tách biệt theo vai trò:
* **Tài khoản ứng dụng demo:** Lưu trữ hạ tầng production, tích hợp CI/CD qua CodePipeline, sử dụng CloudWatch, EventBridge và Lambda webhook handler để phát hiện bất thường và chuyển tiếp sự cố.
* **Tài khoản Splunk:** Đảm nhận tổng hợp và phân tích log tập trung, kết nối riêng tư với tài khoản ứng dụng thông qua VPC peering.
* **Tài khoản AWS DevOps Agent:** Chứa engine điều tra tự động, tiếp nhận webhook sự cố, tương quan dữ liệu từ CloudWatch, Splunk và GitHub, sau đó gửi cập nhật điều tra theo thời gian thực về Slack.

### 2. Luồng xử lý sự cố
**Luồng tự động:**  
`CloudWatch Alarm → EventBridge → Lambda → DevOps Agent Webhook → Điều tra đa nguồn (Splunk, GitHub, CloudWatch) → Root Cause + Mitigation Plan → Slack`

Khi một alarm CloudWatch kích hoạt, EventBridge gọi Lambda để gửi payload sự cố đến webhook của DevOps Agent. Agent lập tức truy vấn log qua Splunk MCP, lấy lịch sử triển khai từ GitHub, rồi đối chiếu các chỉ số CloudWatch với sự kiện deploy để dựng lại bức tranh tổng thể của hệ thống (application topology). Từ đó, agent phân tích mối quan hệ thời gian giữa các lần deploy và sự cố vận hành, xác định nguyên nhân gốc rễ, và sinh ra mitigation plan chi tiết kèm bước khắc phục, tiêu chí thành công và quy trình rollback — tất cả được đăng lên Slack để kỹ sư trực ca "thức dậy với nguyên nhân đã xác định, thay vì một sự cố còn đang diễn ra".

### 3. Các thành phần cấu hình chính
* **Agent Space:** Định nghĩa phạm vi công cụ và hạ tầng mà agent được truy cập, tạo qua Console hoặc AWS CLI.
* **Tích hợp Splunk:** Bật Splunk MCP Server, cấu hình token xác thực và sử dụng Better Webhooks để gửi cảnh báo theo đúng định dạng schema của DevOps Agent.
* **Tích hợp Slack:** Cho phép agent giao tiếp trực tiếp trong kênh làm việc của đội SRE.
* **Tích hợp GitHub:** Kết nối qua OAuth (quyền đọc) giúp agent đối chiếu thay đổi mã nguồn với sự cố vận hành.
* **DevOps Agent Skills:** Cho phép định nghĩa bộ quy tắc điều tra riêng (ví dụ: Dynatrace cho alarm, Splunk cho log, CloudWatch cho serverless).

### 4. Từ chẩn đoán đến khắc phục
Sau khi xác định nguyên nhân gốc rễ, agent sinh mitigation plan theo 4 giai đoạn: **Prepare**, **Pre-Validate**, **Apply** và **Post-Validate**. Đặc biệt, với các fix ở cấp độ code, agent tạo ra "agent-ready spec" — một bộ hướng dẫn có cấu trúc để bàn giao trực tiếp cho coding agent (như Kiro) triển khai thay đổi vào codebase, khép kín hoàn toàn vòng lặp từ chẩn đoán đến vá lỗi.

### 5. Kết luận
Nhờ sự kết hợp của Agent Space, tích hợp đa nguồn và bàn giao agent-ready spec cho coding agent, quy trình SRE chuyển đổi hoàn toàn từ chữa cháy bị động sang xử lý tự động chủ động, rút ngắn MTTR từ hàng giờ xuống còn vài phút.

---

### Hình ảnh & Minh họa
<div align="center">

![Solution Architecture](/images/3-BlogsPosted/3.2-Blog2/solution_architecture.png)

<p style="font-size: 1.15rem; font-weight: 600; margin-top: 8px;">
<i>Figure 1: Solution Architecture</i>
</p>

</div>

### Link bài viết & Tham khảo
* **Link bài viết gốc (AWS Blog):** [https://aws.amazon.com/blogs/devops/building-an-end-to-end-agentic-sre-using-aws-devops-agent/](https://aws.amazon.com/blogs/devops/building-an-end-to-end-agentic-sre-using-aws-devops-agent/)