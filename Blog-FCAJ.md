# AMAZON BEDROCK VÀ NOVA PRO: PHÂN TÍCH SỰ CỐ VẬN HÀNH BẰNG AI ĐA PHƯƠNG THỨC

*Khi một ứng dụng cloud-native gặp sự cố, đội ngũ vận hành thường phải rà soát hàng loạt nguồn dữ liệu quan sát (observability) khác nhau trong áp lực khôi phục dịch vụ càng nhanh càng tốt. Bài viết giới thiệu cách kết hợp Amazon Bedrock và Amazon Nova Pro để xây dựng hệ thống phân tích sự cố tự động, có khả năng xử lý đồng thời cả dữ liệu văn bản lẫn hình ảnh.*

**BÀI TOÁN VẬN HÀNH:**

Các công cụ giám sát truyền thống chỉ dừng lại ở việc cảnh báo khi sự cố xảy ra, còn việc phân tích và tương quan dữ liệu phức tạp vẫn phải dựa vào con người. Quá trình này vốn tốn nhiều thời gian và dễ sai sót, khiến thời gian downtime kéo dài và ảnh hưởng đến trải nghiệm khách hàng. Bài toán đặt ra là làm sao tự động hóa được bước phân tích này mà không đòi hỏi đội ngũ vận hành phải có chuyên môn sâu về machine learning hay data science.

**CƠ CHẾ HOẠT ĐỘNG:**

Nguồn dữ liệu quan sát (CloudWatch, Config, X-Ray, sơ đồ kiến trúc) → Thu thập & lưu trữ (Amazon S3) → Phân tích đa phương thức (Amazon Bedrock + Nova Pro) → Insight & đề xuất khắc phục

Hệ thống vận hành theo bốn giai đoạn chính. Trước tiên, dữ liệu được thu thập và tương quan từ nhiều nguồn hạ tầng khác nhau: chỉ số từ Amazon CloudWatch, lịch sử thay đổi cấu hình từ AWS Config, và các dấu vết request (traces) từ AWS X-Ray. Khi sự cố xảy ra, một script thu thập dữ liệu sẽ chụp lại toàn bộ thông tin liên quan trong khoảng thời gian xảy ra outage và lưu vào Amazon S3 để chuẩn bị phân tích.

Ở bước tiếp theo, một script gọi đến Amazon Bedrock với model Amazon Nova Pro — mô hình có khả năng xử lý đa phương thức (multimodal), tức đọc hiểu được cả dữ liệu văn bản (log, metric) lẫn dữ liệu hình ảnh (sơ đồ kiến trúc hệ thống) trong cùng một lần suy luận. Nhờ vậy, mô hình không chỉ phân tích số liệu thô mà còn "nhìn" được cấu trúc hệ thống để hiểu bối cảnh sự cố sâu hơn.

Kết quả đầu ra là một bộ insight toàn diện: danh sách các nguyên nhân khả nghi được xếp hạng theo xác suất, các bước xử lý sự cố cụ thể, và thậm chí cả nội dung thông báo gợi ý để gửi đến khách hàng — giúp đội vận hành nhanh chóng áp dụng bản sửa lỗi và rút ngắn đáng kể Mean Time to Resolution (MTTR).

**QUY TRÌNH TRIỂN KHAI THỰC NGHIỆM:**

Để minh họa cụ thể, bài viết sử dụng PetShop làm ví dụ. Sau khi thiết lập Amazon S3 bucket để lưu dữ liệu quan sát và sơ đồ kiến trúc ứng dụng, sự cố được giả lập bằng cách thay đổi rule của security group trên load balancer để chặn traffic HTTP. Script thu thập dữ liệu sau đó chạy để lấy chỉ số CloudWatch, thay đổi cấu hình từ AWS Config và trace từ X-Ray, tải toàn bộ lên S3. Cuối cùng, script phân tích gọi Amazon Bedrock với Nova Pro để xử lý dữ liệu đa phương thức và xuất ra khuyến nghị khắc phục.

**KẾT LUẬN:**

Việc kết hợp các dịch vụ observability của AWS với generative AI mở ra một hướng tiếp cận mới cho công tác phản ứng sự cố: tự động hóa bước phân tích dữ liệu đa chiều vốn tốn nhiều thời gian nhất, đồng thời nâng cao chất lượng giao tiếp với khách hàng trong quá trình xử lý sự cố. Đây không chỉ là giải pháp cho các thách thức vận hành hiện tại, mà còn có khả năng mở rộng để đáp ứng độ phức tạp ngày càng tăng của hạ tầng cloud hiện đại. Khi các mô hình nền tảng (foundation models) tiếp tục phát triển, khả năng thấu hiểu hệ thống phức tạp và đưa ra insight hữu ích của chúng sẽ còn được cải thiện hơn nữa.

**LINK THAM KHẢO:**

<https://aws.amazon.com/blogs/mt/using-amazon-bedrock-and-amazon-nova-for-ai-powered-incident-response/>

---

# XÂY DỰNG END-TO-END AGENTIC SRE VỚI AWS DEVOPS AGENT

*Với các hệ thống hiện đại gồm serverless function, microservice và kiến trúc hướng sự kiện, việc phản ứng sự cố ngày càng phức tạp: kỹ sư phải tự tương quan dữ liệu từ nhiều công cụ giám sát khác nhau trong khi chạy đua với SLA. AWS DevOps Agent hướng đến việc thay đổi hoàn toàn cách vận hành này -- hoạt động như một tác nhân AI tự động, luôn túc trực, điều tra sự cố ngay khi xảy ra và hỗ trợ cả môi trường multi-cloud lẫn hybrid, không chỉ riêng AWS.*

**KIẾN TRÚC TRIỂN KHAI:**

Giải pháp được tổ chức trên ba tài khoản AWS tách biệt theo vai trò. Tài khoản ứng dụng demo lưu trữ hạ tầng production, tích hợp CI/CD qua CodePipeline và dùng CloudWatch, EventBridge cùng một Lambda webhook handler để phát hiện bất thường và chuyển tiếp sự cố. Tài khoản Splunk đảm nhận việc tổng hợp và phân tích log tập trung, kết nối riêng tư với tài khoản ứng dụng qua VPC peering. Tài khoản AWS DevOps Agent chứa engine điều tra tự động, tiếp nhận webhook sự cố, tương quan dữ liệu từ CloudWatch, Splunk và GitHub, sau đó gửi cập nhật điều tra theo thời gian thực về Slack.

**LUỒNG XỬ LÝ SỰ CỐ:**

CloudWatch Alarm → EventBridge → Lambda → DevOps Agent Webhook → Điều tra đa nguồn (Splunk, GitHub, CloudWatch) → Root Cause + Mitigation Plan → Slack

Khi một alarm CloudWatch kích hoạt, EventBridge gọi Lambda để gửi payload sự cố đến webhook của DevOps Agent. Agent lập tức truy vấn log qua Splunk MCP, lấy lịch sử triển khai từ GitHub, rồi đối chiếu các chỉ số CloudWatch với sự kiện deploy để dựng lại bức tranh tổng thể của hệ thống (application topology). Từ đó, agent phân tích mối quan hệ thời gian giữa các lần deploy và sự cố vận hành, xác định nguyên nhân gốc rễ, và sinh ra mitigation plan chi tiết kèm bước khắc phục, tiêu chí thành công và quy trình rollback — tất cả được đăng lên Slack để kỹ sư trực ca "thức dậy với nguyên nhân đã xác định, thay vì một sự cố còn đang diễn ra".

**CÁC THÀNH PHẦN CẤU HÌNH CHÍNH:**

Agent Space đóng vai trò định nghĩa phạm vi công cụ và hạ tầng mà agent được truy cập, có thể tạo qua console hoặc AWS CLI. Việc tích hợp Splunk đòi hỏi bật Splunk MCP Server, cấu hình token xác thực, và dùng Better Webhooks (vì webhook mặc định của Splunk không hỗ trợ header/xác thực) để gửi cảnh báo về đúng định dạng schema của DevOps Agent. Tích hợp Slack cho phép agent giao tiếp trực tiếp trong kênh làm việc của đội SRE, trong khi tích hợp GitHub (qua OAuth, quyền đọc) giúp agent đối chiếu thay đổi mã nguồn với sự cố vận hành. Ngoài ra, DevOps Agent Skills cho phép định nghĩa các bộ quy tắc điều tra riêng — ví dụ chỉ định dùng Dynatrace cho alarm, Splunk cho log, CloudWatch cho serverless — nhằm tăng tốc độ và độ chính xác khi xử lý sự cố.

**TỪ CHẨN ĐOÁN ĐẾN KHẮC PHỤC:**

Sau khi xác định nguyên nhân gốc rễ, agent có thể sinh mitigation plan theo bốn giai đoạn: Prepare, Pre-Validate, Apply và Post-Validate, kèm theo các lệnh cụ thể để cập nhật infrastructure-as-code hoặc cấu hình. Đặc biệt, với các fix ở cấp độ code, agent tạo ra "agent-ready spec" — một bộ hướng dẫn có cấu trúc để bàn giao trực tiếp cho một coding agent (như Kiro) triển khai thay đổi vào codebase, khép kín hoàn toàn vòng lặp từ chẩn đoán đến vá lỗi mà không cần con người dịch lại các bước khắc phục thành code.

**KẾT LUẬN:**

Việc kết hợp Agent Space, tích hợp đa nguồn (CloudWatch, Splunk, GitHub, Slack), webhook tự động và bàn giao agent-ready spec cho coding agent đã chuyển đổi hoàn toàn cách vận hành SRE — từ chữa cháy bị động sang xử lý tự động chủ động, rút ngắn MTTR từ hàng giờ xuống còn vài phút, đồng thời giải phóng kỹ sư để tập trung vào đổi mới thay vì túc trực xử lý sự cố.

**LINK THAM KHẢO:**

<https://aws.amazon.com/blogs/devops/building-an-end-to-end-agentic-sre-using-aws-devops-agent/>

---

# TỐI ƯU CHI PHÍ EC2 VỚI AWS COMPUTE OPTIMIZER RIGHT SIZING

*Rightsizing -- điều chỉnh instance type và kích thước sao cho khớp với nhu cầu tài nguyên thực tế -- là một trong những cách hiệu quả nhất để cải thiện ROI cho khoản đầu tư EC2. Nhưng thực hiện thủ công trên hàng trăm, hàng nghìn instance vừa tốn thời gian vừa dễ sai sót. AWS Compute Optimizer giải quyết bài toán này bằng cách phân tích cấu hình và mức sử dụng tài nguyên để đưa ra khuyến nghị rightsizing dựa trên dữ liệu.*

**BÀI TOÁN VẬN HÀNH:**

Phần lớn tổ chức không có cái nhìn rõ ràng về tỷ lệ hiệu năng-chi phí tối ưu cho instance của mình, dẫn đến hai thái cực: hoặc overprovisioning gây lãng phí chi phí, hoặc undersizing gây rủi ro suy giảm hiệu năng. Compute Optimizer trả lời câu hỏi này bằng cách phân tích tới 93 ngày dữ liệu sử dụng từ CloudWatch, từ đó phân loại từng instance thành: **Over-provisioned** (dư thừa tài nguyên, có thể downsize), **Under-provisioned** (thiếu tài nguyên, rủi ro hiệu năng), **Optimized** (đã phù hợp), và **Idle** (gần như không sử dụng, nên terminate hoặc gộp lại).

**CÁC CHỈ SỐ ĐƯỢC PHÂN TÍCH:**

Compute Optimizer đánh giá dựa trên CPU utilization, memory utilization (khi được bật), network I/O, disk I/O, throughput/IOPS của EBS, và GPU utilization (nếu có). Với mỗi finding, hệ thống đề xuất tối đa ba lựa chọn thay thế, xếp hạng theo mức tiết kiệm ước tính, rủi ro hiệu năng và mức độ nỗ lực di chuyển (migration effort) — từ Very low (cùng kiến trúc CPU) đến High (khác kiến trúc, chưa có phiên bản tương thích).

**5 BEST PRACTICE ĐÁNG CHÚ Ý:**

1. **Bật Cost Optimization Hub để có ước tính tiết kiệm sau chiết khấu:** khi bật, Compute Optimizer tự động chuyển sang chế độ AfterDiscounts, tính đến các cam kết Savings Plans hay Reserved Instances hiện có, giúp con số tiết kiệm phản ánh đúng thực tế thay vì giá On-Demand.

2. **Bật memory metrics để khuyến nghị chính xác hơn:** vì CloudWatch không thu thập memory mặc định, việc bổ sung qua CloudWatch Agent hoặc tích hợp bên thứ ba (Datadog, Dynatrace, Instana, New Relic) giúp Compute Optimizer có bức tranh đầy đủ hơn, đặc biệt quan trọng với workload nặng về memory như database hay ứng dụng JVM.

3. **Tùy chỉnh preference theo chiến lược riêng:** có thể điều chỉnh ngưỡng CPU utilization (P90/P95/P99.5), headroom cho CPU và memory, lookback period (14/32/93 ngày), hay giới hạn instance type theo cam kết mua sẵn — áp dụng ở cấp tổ chức, tài khoản hoặc khu vực.

4. **Đánh giá kỹ khuyến nghị Graviton:** chuyển sang Graviton (ARM64) có thể cải thiện tới 40% tỷ lệ giá/hiệu năng, nhưng cần xác minh khả năng tương thích kiến trúc, kiểm tra dependency bên thứ ba, và test trên môi trường staging trước khi áp dụng cho production.

5. **Xây dựng quy trình rightsizing bài bản:** thiết lập chu kỳ review định kỳ, ưu tiên instance có mức tiết kiệm cao và rủi ro thấp, xác nhận lại với chủ sở hữu ứng dụng, và theo dõi kết quả thực tế qua Cost Explorer. Với tổ chức muốn tự động hóa xa hơn, AWS cung cấp kiến trúc tham khảo dùng Step Functions, EventBridge và Lambda để tự động triển khai khuyến nghị.

**KẾT LUẬN:**

AWS Compute Optimizer cung cấp nền tảng dữ liệu vững chắc để ra quyết định rightsizing một cách khoa học. Bằng cách bật đầy đủ chỉ số memory, tùy chỉnh preference theo đặc thù workload, đánh giá thận trọng các lựa chọn Graviton, và duy trì quy trình review có hệ thống, tổ chức có thể tối ưu đội instance EC2 của mình — vừa giảm chi phí, vừa đảm bảo hiệu năng cần thiết.

**LINK THAM KHẢO:**

<https://aws.amazon.com/blogs/compute/optimize-ec2-costs-with-aws-compute-optimizer-right-sizing/>
