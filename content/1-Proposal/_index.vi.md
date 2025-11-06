---
title: "Đề Án"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

# SorcererXStreme: Nền tảng Hướng dẫn Siêu hình Ứng dụng AI

## 1. Tóm tắt  

Nền tảng SorcererXStreme AI là một hệ thống hướng dẫn tâm linh thống nhất do AI điều khiển, được thiết kế để giúp người dùng khám phá bản thân thông qua nhiều lĩnh vực huyền học Đông và Tây khác nhau, bao gồm Chiêm tinh học (Astrology), Tarot, Thần số học (Numerology) và Tử vi Phương Đông (Eastern Horoscopes). Nền tảng của hệ thống là Lõi Tạo sinh Tăng cường Truy xuất (Retrieval-Augmented Generation - RAG Core), đảm bảo tất cả đầu ra đều dựa trên các nguồn tri thức huyền học được chọn lọc.

## 2. Phát biểu Vấn đề 

### Vấn đề là gì?

Người dùng hiện đang phải đối mặt với một số hạn chế khi khám phá kiến thức tâm linh và siêu hình:

*   **Thông tin Phân mảnh và Chưa được Xác minh:** Thông tin rải rác trên internet và thường thiếu độ tin cậy hoặc sự đối chiếu thích hợp.
*   **Khó khăn trong Việc So sánh Đa ngành:** Kết quả khó so sánh giữa các trường phái tư tưởng Phương Đông (ví dụ: Tử vi Phương Đông) và Phương Tây (ví dụ: Chiêm tinh học).
*   **Thiếu Cá nhân hóa và Tương tác:** Hầu hết các ứng dụng cung cấp các bài đọc tĩnh, thiếu chiều sâu của đối thoại cá nhân hóa và lời khuyên theo ngữ cảnh.
*   **Nội dung Nông:** Nhiều ứng dụng "vui" thiếu chiều sâu trí tuệ và kiến thức vững chắc.

### Giải pháp

SorcererXStreme AI cung cấp một nền tảng thống nhất, trực quan và thông minh:

*   **Tương tác Trực tiếp:** Người dùng trò chuyện trực tiếp với AI Chatbot, hỏi bất cứ điều gì về tính cách, vận mệnh hoặc các mối quan hệ của họ.
*   **Luận giải Dựa trên RAG (RAG-Grounded Interpretations):** Hệ thống RAG cốt lõi đảm bảo rằng các luận giải dựa trên dữ liệu huyền học đã được xác minh, đảm bảo độ chính xác và chiều sâu.
*   **Trải nghiệm Người dùng Phân tầng:** Các tầng Miễn phí (Free) và VIP tối ưu hóa trải nghiệm người dùng và tạo ra một luồng doanh thu.
*   **Thiết kế Hiệu quả về Chi phí:** Một thiết kế hiện đại, nhẹ được triển khai nhanh chóng trên kiến trúc serverless AWS tối ưu hóa chi phí.

### Lợi ích và Lợi tức Đầu tư (Return on Investment)

| Lợi ích              | Tác động                                                             | Giá trị                                        |
| :--------------------: | :------------------------------------------------------------------: | :--------------------------------------------: |
| **Độ tin cậy Dữ liệu** | RAG giảm "ảo giác" của AI và cung cấp các luận giải có thể xác minh. | Độ tin cậy Cao & giữ chân người dùng tốt hơn.  |
| **Tính Trung tâm**     | Hợp nhất dữ liệu huyền học Đông và Tây trong một nền tảng.           | Cơ sở Tri thức Thống nhất cho người dùng.      |
| **Khả năng Kiếm tiền** | Mô hình đăng ký VIP mở khóa các tính năng nâng cao.                  | Dòng Doanh thu Ổn định và khả năng kinh doanh. |
| **Chi phí Vận hành**   | Kiến trúc serverless AWS được sử dụng.                               | Ước tính $15–$35/tháng cho MVP.                |

## 3. Kiến trúc Giải pháp (Solution Architecture)

Nền tảng SorcererXStreme AI sử dụng kiến trúc serverless lai (hybrid serverless) mạnh mẽ trên AWS, được thiết kế tỉ mỉ để xử lý các tương tác người dùng theo thời gian thực, các tác vụ theo lịch trình và giám sát tự động. Thiết kế toàn diện này đảm bảo tính toán chuyên biệt, khả năng mở rộng cao và bảo mật nghiêm ngặt trên tất cả các luồng chức năng.

![Sơ đồ kiến trúc](/images/architecture.jpg)


### Các Dịch vụ AWS Được Sử dụng

| Lớp                       | Dịch vụ AWS                         | Vai trò Chính trong SorcererXStreme AI                                                                                                                                                                                              |
| :-----------------------: | :---------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| **Mạng & Biên**           | Route 53, CloudFront, WAF           | Route 53 xử lý định tuyến DNS. CloudFront (CDN) tăng tốc phân phối nội dung. WAF cung cấp tính năng lọc lưu lượng và bảo mật chống lại các khai thác web.                                                                           |
| **Bảo mật & Danh tính**   | Cognito, Secrets Manager            | Cognito quản lý xác thực và ủy quyền người dùng. Secrets Manager lưu trữ và quản lý an toàn các thông tin xác thực nhạy cảm.                                                                                                        |
| **Tính toán (API)**       | App Runner, API Gateway, AWS Lambda | App Runner host frontend Next.js hoặc các containers backend cốt lõi. API Gateway hoạt động như điểm vào đồng bộ, định tuyến các yêu cầu đến các Lambda Functions chuyên dụng (Chatbot, Metaphysical API, History API).             |
| **Bất đồng bộ & Sự kiện** | EventBridge Scheduler, SQS, SES     | EventBridge Scheduler kích hoạt chức năng tử vi hàng ngày. SQS đệm và tách rời việc xử lý tin nhắn (fan-out/fan-in) cho các lời nhắc. SES gửi email thông báo cho người dùng.                                                       |
| **Tầng AI/ML**            | Amazon Bedrock                      | Cung cấp quyền truy cập được quản lý vào các Mô hình Nền tảng (LLMs) cho chatbot AI Prophet, xử lý ngữ cảnh RAG và tạo nội dung.                                                                                                    |
| **Dữ liệu & Lưu trữ**     | RDS for PostgreSQL, DynamoDB, S3    | RDS lưu trữ dữ liệu quan hệ (hồ sơ người dùng chi tiết, danh sách người dùng cho lời nhắc). DynamoDB lưu trữ dữ liệu truy cập nhanh, tần suất cao (Lịch sử Chat, Lịch sử Luận giải). S3 lưu trữ tài sản tĩnh và cơ sở tri thức RAG. |
| **Giám sát & DevOps**     | CloudWatch, SNS, CodePipeline       | CloudWatch thu thập nhật ký (logs) và số liệu (metrics). SNS gửi cảnh báo quan trọng đến các nhà phát triển. CodePipeline/CodeBuild quản lý quy trình CI/CD từ GitHub đến triển khai.                                               |

### Thiết kế Thành phần

Nền tảng hoạt động thông qua bốn luồng chức năng riêng biệt, liên kết với nhau:

**1. Tương tác API Thời gian Thực (Luồng Đồng bộ)**

*   **Điểm vào Yêu cầu (Request Entry):** Yêu cầu của người dùng đi vào qua Route 53 → CloudFront → WAF.
*   **Định tuyến & Logic (4):** API Gateway định tuyến các yêu cầu đến Lambda function thích hợp.
    *   Lambda Chatbot Đọc/Ghi lịch sử trò chuyện từ DynamoDB để duy trì ngữ cảnh, sau đó gọi Bedrock.
    *   Lambda Metaphysical API thực hiện các phép tính phức tạp, gọi Bedrock và Lưu Lịch sử (DynamoDB).
*   **Bảo mật (3):** Tất cả các Lambda truy cập Secrets Manager để truy xuất thông tin xác thực cần thiết một cách an toàn.

**2. Thông báo Tử vi Hàng ngày (Luồng Bất đồng bộ)**

*   **Kích hoạt (6):** EventBridge Scheduler kích hoạt vào một thời điểm đã định (ví dụ: 8:00 sáng), kích hoạt TriggerReminderLambda.
*   **Phân tán (Fan-Out) (7):** Lambda này đọc danh sách người dùng từ RDS và gửi các tin nhắn riêng lẻ (ID người dùng, email) đến Hàng đợi Lời nhắc SQS (SQS Reminder Queue).
*   **Phân phối (Delivery) (8):** SendReminderLambda kéo các tin nhắn từ SQS, tạo nội dung thông báo và gửi email qua Amazon SES.

**3. Luồng Giám sát & Cảnh báo**

*   **Ghi nhật ký (Logging) (9):** Tất cả các dịch vụ đẩy nhật ký và số liệu đến CloudWatch.
*   **Cảnh báo:** CloudWatch Alarm giám sát các số liệu quan trọng và sử dụng Amazon SNS để thông báo cho nhà phát triển về các sự cố nghiêm trọng.

**4. DevOps (Luồng CI/CD)**

*   **Cập nhật Mã (Code Update) (10):** Các nhà phát triển đẩy mã lên GitHub, kích hoạt chuỗi CodePipeline/CodeBuild. Pipeline tự động đóng gói và triển khai mã được cập nhật đến Tầng Tính toán (Compute Layer) (Lambda, App Runner), đảm bảo cập nhật không bị gián đoạn.

## 4. Triển khai Kỹ thuật (Technical Implementation)

Dự án SorcererXStreme sẽ tuân theo phương pháp **Phát triển Lặp lại - Linh hoạt (Agile-Iterative Development)**, tập trung vào việc cung cấp một phần gia tăng hoạt động với vai trò người dùng mở rộng và tích hợp RAG trong mỗi chu kỳ. Việc phát triển được cơ cấu thành một **lộ trình 9 tuần** bao gồm ba lần lặp chính (Iter 3, 4 và 5) sau giai đoạn lập kế hoạch ban đầu.

### Các Giai đoạn Triển khai

Quá trình phát triển bao gồm bốn giai đoạn chính, được chia thành ba lần lặp tập trung kéo dài 2 tuần:

| Giai đoạn                                   | Thời gian      | Lĩnh vực Tập trung (Focus Area)                                                                                                      |
| :-----------------------------------------: | :------------: | :----------------------------------------------------------------------------------------------------------------------------------: |
| **I. Phân tích Yêu cầu & Tài liệu (Iter3)** | 3 Tuần         | Hoàn thiện tài liệu SRS (v2) và SDS (v2), đề xuất, đặt nền tảng cho vai trò mở rộng và RAG.                                          |
| **II. Thiết kế & Mở rộng (Iter 4)**         | 3 Tuần         | Phát triển cốt lõi của pipeline RAG, triển khai hệ thống Vai trò Người dùng (Guest/Free/VIP), và cấu hình cơ sở hạ tầng AWS cốt lõi. |
| **III. Tích hợp AWS & Kiểm thử (Iter 5)**   | 3 Tuần         | Triển khai hoàn chỉnh trên AWS, kiểm thử đầu cuối, và tối ưu hóa hiệu suất.                                                          |
| **IV. Đánh giá & Bàn giao (Handoff)**       | Đang tiếp diễn | Tối ưu hóa, báo cáo hiệu suất và chuẩn bị phát hành beta cuối cùng.                                                                  |

### Yêu cầu Kỹ thuật & Sản phẩm Bàn giao theo Lần lặp

**Lần lặp 3 – Tích hợp RAG & Thiết kế lại Hệ thống (Tuần 1–2–3)**

**Mục tiêu:** Phân tích lại các yêu cầu, hoàn thiện kiến trúc AWS, xác định các luồng trải nghiệm người dùng và tạo mẫu thiết kế RAG.

| Hạng mục               | Các Nhiệm vụ Chính (Key Tasks)                                                                                                                                                             | Trách nhiệm |
| :--------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------: |
| **Tài liệu Hệ thống**  | Xem xét và cập nhật kiến trúc hiện có. Viết **SRS v2** (Chức năng & Phi chức năng) và **SDS v2**.                                                                                          | SE          |
| **UX & Luồng Vai trò** | Thiết kế các luồng người dùng chi tiết cho quá trình chuyển đổi **Khách/Miễn phí/VIP**. Xác định giới hạn chức năng cho mỗi vai trò. Đề xuất **Giao diện nâng cấp VIP**.                   | SE          |
| **Kiến trúc RAG**      | Đề xuất cơ chế RAG (nguồn dữ liệu, pipeline, lưu trữ embedding). Thiết kế pipeline RAG nguyên mẫu: văn bản -\> embedding -\> chỉ mục. **Thu thập Dữ liệu** (Tarot, Horoscope, Numerology). | AI          |
| **Cơ sở hạ tầng AWS**  | Hoàn thiện **Sơ đồ Kiến trúc AWS** (Amplify, Lambda, DynamoDB, Cognito, S3). Tính toán **Ước tính Chi phí** tập trung vào các tùy chọn Miễn phí (Free-tier) và Serverless.                 | SE, AI      |

**Sản phẩm Bàn giao:** Hoàn thành SRS v2, SDS v2, Sơ đồ Kiến trúc AWS kèm Ước tính Chi phí, tài liệu Luồng UX/Vai trò và thiết kế nguyên mẫu RAG.

**Lần lặp 4 – Vai trò Người dùng & Pipeline RAG Sản xuất (Tuần 4–5–6)**

**Mục tiêu:** Triển khai hệ thống ủy quyền người dùng và tích hợp corpus dữ liệu RAG nền tảng.

| Hạng mục                  | Các Nhiệm vụ Chính                                                                                                                                              | Trách nhiệm |
| :-----------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------: |
| **Xác thực & Vai trò**    | Thiết kế lược đồ người dùng (khách, miễn phí, vip). Tích hợp **AWS Cognito** vào frontend. Xác định quyền truy cập API dựa trên vai trò người dùng.             | SE          |
| **Chức năng VIP**         | Triển khai logic cho việc **giới hạn số lần trò chuyện, rút bài Tarot,** và chế độ xem Chiêm tinh chi tiết. Triển khai mô hình định giá và màn hình nâng cấp.   | SE          |
| **Chuẩn bị Sản xuất RAG** | Làm sạch và chuẩn hóa dữ liệu. Triển khai truy xuất ngữ cảnh theo chủ đề (tình yêu, sự nghiệp, cung hoàng đạo). Xây dựng và lưu trữ **Corpus ban đầu trên S3**. | AI          |
| **Tối ưu hóa AI**         | Tinh chỉnh mô hình embedding và kích thước chunk. Viết script cho **cập nhật dữ liệu tự động** (S3 -\> index).                                                  | AI          |

**Sản phẩm Bàn giao:** Hệ thống vai trò người dùng (Guest/Free/VIP) hoạt động đầy đủ được tích hợp với Cognito. Các điểm cuối API RAG mock hoạt động trên môi trường cục bộ/phát triển, cho phép kiểm thử logic truy cập VIP.

**Lần lặp 5 – Triển khai AWS & Đánh giá (Tuần 7 – 8 – 9)**

**Mục tiêu:** Hoàn thành triển khai đầy đủ trên đám mây, thực hiện kiểm thử toàn diện và chuẩn bị cho phát hành công khai.

| Hạng mục                   | Các Nhiệm vụ Chính                                                                                                                                                                       | Trách nhiệm |
| :------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------: |
| **Cơ sở hạ tầng AWS**      | Cấu hình cuối cùng của **App Runner + Lambda**. Triển khai **DynamoDB, S3, Cognito**. Tạo **Chính sách IAM** tối thiểu.                                                                  | SE          |
| **Giám sát & Ghi nhật ký** | Thiết lập **CloudWatch** cho việc ghi nhật ký của Lambda và Cognito. Tạo bảng điều khiển để giám sát mức sử dụng và chi phí.                                                             | SE          |
| **Tinh chỉnh Mô hình AI**  | Tối ưu hóa **lời nhắc LLM (LLM prompt)** và pipeline RAG. Triển khai các cơ chế **kiểm soát token LLM** để quản lý chi phí.                                                              | AI          |
| **Kiểm thử & Đánh giá**    | Viết **các trường hợp kiểm thử đầu cuối (end-to-end test cases)**. Kiểm thử toàn diện các vai trò, giới hạn VIP và độ chính xác của RAG. Báo cáo về độ chính xác của AI (trước/sau RAG). | AI          |

**Sản phẩm Bàn giao:** Hệ thống ổn định chạy trên cơ sở hạ tầng AWS. Báo cáo hiệu suất, chi phí và kiểm thử (**AWS Service Cost and Performance Sheet**). Sẵn sàng cho việc kiểm thử Beta công khai.

## 5. Mốc thời gian & Các cột mốc (Timeline & Milestones)

Dự án SorcererXStreme sẽ được thực hiện trong **khoảng thời gian phát triển tập trung 9 tuần** theo mô hình Lặp lại - Linh hoạt (Agile-Iterative) để nhanh chóng cung cấp một MVP với các tính năng chính như **lõi RAG** và **hệ thống người dùng VIP**.

### Mốc thời gian Dự án

| Lần lặp                                  | Thời gian | Tuần          | Trọng tâm Chính                         | Các Sản phẩm Bàn giao Chính (Cột mốc)                                                                                                                                                 |
| :--------------------------------------: | :-------: | :-----------: | :-------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| **Lặp 3: Thiết kế lại & Nguyên mẫu RAG** | 3 Tuần    | 1 – 2 **–** 3 | **Thiết kế Nền tảng & Tài liệu**        | **SRS v2** và **SDS v2, Đề xuất** được hoàn thiện. **Sơ đồ Kiến trúc AWS** kèm Ước tính Chi phí đã sẵn sàng. Dữ liệu RAG được thu thập và pipeline ban đầu được thiết kế.             |
| **Lặp 4: Vai trò & Hệ thống VIP**        | 3 Tuần    | 4 – 5 – 6     | **Triển khai Logic Cốt lõi & Ủy quyền** | **AWS Cognito** được tích hợp để xác thực người dùng. Logic vai trò **Khách/Miễn phí/VIP** đầy đủ được triển khai và có thể kiểm thử. Corpus dữ liệu RAG được xây dựng trên S3.       |
| **Lặp 5: Triển khai AWS & QA**           | 3 Tuần    | 7 – 8 – 9     | **Triển khai Đám mây & Ổn định**        | Hệ thống chạy **ổn định trên AWS** (Amplify, Lambda, DynamoDB). Hoàn thành kiểm thử đầu cuối đầy đủ. **AWS Cost and Performance Sheet** được hoàn thiện. Sẵn sàng cho Phát hành Beta. |

## 6. Ước tính Ngân sách (Budget Estimation)

Dự án được cơ cấu để hoạt động chủ yếu trong **Tầng Miễn phí AWS (AWS Free Tier)** trong 12 tháng đầu tiên, dẫn đến chi phí vận hành cực kỳ thấp. Chúng tôi giả định mức sử dụng thấp cho môi trường demo/MVP không sản xuất (khoảng 5.000 yêu cầu/tháng).

### Chi phí Cơ sở hạ tầng

| Dịch vụ AWS                                  | Lợi ích Miễn phí Hàng tháng                          | Chi phí Ước tính Hàng tháng (USD) | Loại Chi phí     | Ghi chú & Trạng thái Tầng Miễn phí                                         |
| :------------------------------------------: | :--------------------------------------------------: | :-------------------------------: | :--------------: | :------------------------------------------------------------------------: |
| **AWS Lambda** (Tính toán)                   | 1M Yêu cầu & 400K GB-giây                            | **$0.00**                         | Sử dụng          | Hoàn toàn trong giới hạn Tầng Miễn phí.                                    |
| **API Gateway** (Định tuyến)                 | 1 Triệu Yêu cầu                                      | **$0.00**                         | Sử dụng          | Hoàn toàn trong giới hạn Tầng Miễn phí.                                    |
| **DynamoDB** (Lịch sử/Giới hạn Tốc độ)       | 25 GB Lưu trữ & 25M RCU/WCU                          | **$0.00**                         | Sử dụng          | Được bao phủ hoàn toàn bởi Tầng Miễn phí.                                  |
| **Amazon S3** (Cơ sở Tri thức RAG)           | 5 GB Lưu trữ Tiêu chuẩn                              | **$0.00**                         | Sử dụng          | Được bao phủ hoàn toàn bởi Tầng Miễn phí (sử dụng 1 GB).                   |
| **Cognito** (Xác thực)                       | 50.000 MAUs                                          | **$0.00**                         | Sử dụng          | Được bao phủ hoàn toàn bởi Tầng Miễn phí (sử dụng 100 MAUs).               |
| **RDS for PostgreSQL** (t3.micro, Single-AZ) | 750 Giờ/Tháng & 20 GB Lưu trữ                        | **$0.00**                         | Thể hiện/Lưu trữ | Được bao phủ bởi Tầng Miễn phí trong 12 tháng (sử dụng 744 giờ/tháng).     |
| **App Runner** (Host Frontend)               | 14K vCPU-giờ & 52K GB-giờ                            | **$0.00**                         | Thể hiện/Lưu trữ | Được bao phủ bởi Tầng Miễn phí trong 12 tháng.                             |
| **SQS, SES, EventBridge, CloudWatch**        | Giới hạn rộng rãi về yêu cầu, email và nhật ký       | **$0.00**                         | Sử dụng          | Tất cả các dịch vụ bất đồng bộ và giám sát đều được bao phủ.               |
| **Secrets Manager** (RDS/Khóa LLM)           | Dùng thử 30 ngày Miễn phí, sau đó $0.40/secret/tháng | **≈$0.80**                        | **Cố định**      | Chi phí cho việc lưu trữ 2 bí mật. Chi phí cơ sở hạ tầng cố định duy nhất. |

### Tổng Chi phí Dự án

| Hạng mục                                     | Ước tính Chi phí | Mục đích / Cơ chế Kiểm soát                                                                                           |
| :------------------------------------------: | :--------------: | :-------------------------------------------------------------------------------------------------------------------: |
| **Tổng Chi phí Cơ sở hạ tầng**               | **≈$0.80**       | Chỉ **Secrets Manager**. Tất cả các dịch vụ khác là 0.00 USD.                                                         |
| **AI/LLM (Bedrock)**                         | **≈$1.00–$5.00** | Chi phí biến đổi (phụ thuộc vào mức sử dụng). Được kiểm soát bằng **giới hạn token Lambda** và **phân tầng sử dụng**. |
| **Mức trần Ngân sách AI (Giới hạn An toàn)** | **$35.00**       | Chi tiêu tối đa được phân bổ cho AI/LLM để ngăn chặn đột biến chi phí do vòng lặp mã hoặc lạm dụng.                   |
| **Tổng Chi phí Hàng tháng An toàn Tối đa**   | **≈$35.80 USD**  | **Đảm bảo dự án vẫn an toàn dưới ngưỡng $40 USD.** Ngân sách AWS sẽ được đặt ở mức này.                               |

**Kết luận:** Dự án SorcererXStreme AI được thiết kế để ổn định hoạt động và hiệu quả chi phí, với chi phí cơ sở hạ tầng cốt lõi dưới 1 USD và mức trần an toàn là 35.80 USD để ngăn chặn hóa đơn bất ngờ, làm cho nó trở nên lý tưởng cho một bản demo hoặc MVP.

## 7. Đánh giá Rủi ro (Risk Assessment)

### Ma trận Rủi ro

| Rủi ro                              | Tác động   | Xác suất   | Chiến lược Giảm thiểu (Mitigation Strategy)                                                                                                    |
| :---------------------------------: | :--------: | :--------: | :--------------------------------------------------------------------------------------------------------------------------------------------: |
| **Ảo giác LLM (LLM Hallucination)** | Cao        | Trung bình | Triển khai **Bộ kiểm tra Thực tế RAG (RAG Fact Checker)**; sử dụng LLM chất lượng cao; căn cứ câu trả lời vào các nguồn đã được xác minh.      |
| **Vượt chi phí (Các cuộc gọi LLM)** | Cao        | Trung bình | Thiết lập **Cảnh báo Ngân sách AWS (AWS Budget Alerts)**; triển khai **kiểm soát token**; sử dụng mô hình LLM phân tầng (Miễn phí so với VIP). |
| **Độ trễ Truy xuất RAG**            | Trung bình | Trung bình | Tối ưu hóa việc lập chỉ mục RAG (FAISS); tối ưu hóa kích thước chunk và lựa chọn mô hình embedding.                                            |
| **Vi phạm Bảo mật**                 | Cao        | Thấp       | Sử dụng **Cognito** để xác thực và **Secret Manager** để xử lý thông tin xác thực.                                                             |

## 8. Kết quả Mong đợi (Expected Outcomes)

### Cải tiến Kỹ thuật

*   **Độ chính xác theo thời gian thực:** Tích hợp RAG giảm đáng kể "ảo giác" của AI, nâng cao độ tin cậy của các luận giải.
*   **Khả năng mở rộng:** Kiến trúc serverless AWS đảm bảo khả năng mở rộng tự động để xử lý lưu lượng truy cập đáng kể của người dùng.

### Giá trị Dài hạn

*   **Khả năng Kiếm tiền (Monetization):** Mô hình đăng ký VIP tạo ra một con đường rõ ràng, ổn định để tạo doanh thu.
*   **Nền tảng Dữ liệu:** Một cơ sở tri thức huyền học độc quyền, đã được xác minh (corpus RAG) được thiết lập như một tài sản có giá trị, có thể tái sử dụng.
*   **Mở rộng Tương lai:** Kiến trúc AWS linh hoạt (Lambda, Bedrock) dễ dàng nâng cấp cho các ứng dụng di động (React Native) hoặc tính năng trò chuyện bằng giọng nói.


