# DAY21_Track1_2A202602518_NguyenPhamOanhOanh

# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Nguyễn Phạm Oanh Oanh
- MSSV / mã học viên: 2A202602518
- Lớp: Track 1
- Ngành đã chọn: Content creator 

``` markdown
| Nội dung | Đánh giá của tôi và lý do |
| :--- | :--- |
| **Những tác hại chính có thể xảy ra** | - **Xâm phạm hình ảnh, quyền riêng tư và nhân phẩm:** ảnh người thật bị chỉnh sửa thành nội dung tình dục hóa, làm nhục hoặc giả mạo mà họ không biết; người bị mô phỏng, đặc biệt trẻ em, có thể chịu tổn hại danh tiếng và tâm lý ([ICO, 2026](https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/02/ico-announces-investigation-into-grok?utm_source=chatgpt.com)).<br>- **Đánh lừa người xem:** ảnh tổng hợp có thể bị hiểu là bằng chứng của sự kiện hoặc hành vi có thật, ảnh hưởng người được mô tả và niềm tin của công chúng ([European Commission, 2026](https://digital-strategy.ec.europa.eu/en/policies/code-practice-ai-generated-content?utm_source=chatgpt.com)).<br>- **Rủi ro sở hữu trí tuệ:** đầu ra có thể chứa yếu tố được bảo hộ hoặc watermark, khiến creator, nhãn hàng và chủ sở hữu phát sinh tranh chấp ([High Court, 2025](https://www.judiciary.uk/wp-content/uploads/2025/11/Getty-Images-v-Stability-AI.pdf?utm_source=chatgpt.com)).<br>- **Thiên kiến ổn định (Stable bias):** ảnh nghề nghiệp hoặc nhóm xã hội có thể củng cố định kiến và làm các nhóm ít được đại diện tiếp tục bị bỏ qua ([Luccioni et al., 2023](https://arxiv.org/abs/2303.11408?utm_source=chatgpt.com); [NIST, 2024](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf)). |
| **Mức độ high-stakes** | Trung bình - hoạt động sáng tạo thông thường<br>Cao - liên quan người thật, trẻ em hoặc nội dung dễ bị coi là bằng chứng thật, có thể gây hậu quả nghiêm trọng ([NIST, 2024](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf)). |
| **Dữ liệu nhạy cảm có thể được sử dụng** | Dữ liệu có thể gồm: ảnh khuôn mặt và cơ thể; tên, tài khoản và thông tin nhận diện trong prompt/caption; ảnh gia đình; thông tin sức khỏe, đời sống tình dục hoặc tôn giáo được thể hiện trong ảnh; vị trí, thời gian và metadata nếu được giữ lại. Cần xét cả dữ liệu trong dataset huấn luyện.<br>Ảnh đã xuất hiện công khai không chứng minh người trong ảnh đã đồng ý với việc huấn luyện AI hoặc chỉnh sửa ảnh. Cũng cần phân biệt dữ liệu cá nhân với dữ liệu sinh trắc học: ảnh chân dung không tự động là dữ liệu sinh trắc học thuộc nhóm đặc biệt; còn phụ thuộc cách xử lý và mục đích nhận diện ([ICO, 2024](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/lawful-basis/special-category-data/what-is-special-category-data/)). |
| **Nhu cầu human review** | Trung bình, tăng lên Cao về tác động và nhu cầu kiểm soát với nội dung nhạy cảm hoặc phát hành rộng.<br>- Trước khi đưa vào sử dụng: kiểm tra nguồn, quyền sử dụng, dữ liệu trẻ em và các cách lạm dụng có thể dự đoán.<br>- Trước khi xuất bản: creator/editor chịu trách nhiệm duyệt nội dung; chuyển Legal/Privacy khi liên quan người thật, consent hoặc quyền sở hữu; chuyển Trust & Safety khi có dấu hiệu tình dục hóa, đe dọa hay làm nhục. Người duyệt phải kiểm tra bối cảnh, giấy phép và nhãn AI, đồng thời có quyền từ chối xuất bản.<br>- Sau khi xuất bản: Trust & Safety tiếp nhận khiếu nại, đánh giá mức khẩn cấp và phối hợp gỡ bỏ/hạn chế phát tán ([NIST, 2024](https://doi.org/10.6028/NIST.AI.600-1)).<br>- Việc gắn nhãn và lưu provenance hỗ trợ kiểm tra đã có công cụ hỗ trợ, nhưng không thay thế xác minh sự thật hay consent (cần human review), Content Credentials không chứng minh nội dung là đúng sự thật ([C2PA, n.d.](https://spec.c2pa.org/specifications/specifications/2.2/explainer/Explainer.html?utm_source=chatgpt.com)).<br>Với nội dung có dấu hiệu xâm hại rõ ràng, đề xuất là chặn tạo/phát hành; thì human review xử lý trường hợp không rõ và khiếu nại ([NIST, 2024](https://doi.org/10.6028/NIST.AI.600-1)). |

Dưới đây là **Brief Case cho ba case đã chọn**, giữ ngắn và tách rõ bằng chứng với nhận định. LAION là case ở **khâu dữ liệu đầu vào của hệ sinh thái tạo ảnh**, cần ghi rõ phạm vi này trong bài.

### 2. Case 1 — Grok/xAI: tạo và phát tán ảnh tình dục hóa
- **Tổ chức / sản phẩm AI:** xAI — Grok, tích hợp trên X.
- **Thời gian, địa điểm / bối cảnh:** 29/12/2025–08/01/2026; nội dung được đăng công khai trên X, tiếp cận người dùng quốc tế.
- **AI được dùng để làm gì:** Tạo ảnh từ prompt và chỉnh sửa ảnh có sẵn.
- **Vấn đề hoặc sự kiện đáng chú ý:** Grok bị sử dụng để tạo ảnh tình dục hóa người thật, bao gồm người nổi tiếng và người có vẻ là trẻ em. 03/02/2026, ICO mở điều tra X và xAI về xử lý dữ liệu cá nhân và biện pháp bảo vệ trong Grok.
- **Số liệu có nguồn:** CCDH phân tích **20.000 bài đăng chứa ảnh**, lấy mẫu từ **4.621.335 bài đăng** trong 11 ngày trên; từ đó ước tính khoảng **3 triệu ảnh tình dục hóa**, gồm khoảng **23.338 ảnh có vẻ mô tả trẻ em** (CCDH, 2026). [[CCDH](https://counterhate.com/research/grok-floods-x-with-sexualized-images/?utm_source=chatgpt.com)]
- **Nguồn:**
  - **Tài liệu nghiên cứu chính:** [*Grok floods X with sexualized images of women and children*](https://counterhate.com/research/grok-floods-x-with-sexualized-images/?utm_source=chatgpt.com) — Center for Countering Digital Hate — 22/01/2026 — https://counterhate.com/research/grok-floods-x-with-sexualized-images/
  - **Hồ sơ phản ứng quản lý:** [*ICO announces investigation into Grok*](https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/02/ico-announces-investigation-into-grok/?utm_source=chatgpt.com) — ICO — 03/02/2026 — mục **Our investigatory process** — https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/02/ico-announces-investigation-into-grok/
- **Phân biệt bằng chứng và nhận định:**
  - **Bằng chứng:** các con số là ước tính; định nghĩa “tình dục hóa” bao gồm cả đồ bơi/đồ lót. Nghiên cứu không xác định sự đồng thuận và không phân biệt toàn bộ ảnh chỉnh sửa với ảnh tạo mới.
  - **Nhận định của tôi:** case cho thấy rủi ro kết hợp giữa lạm dụng của người dùng và kiểm soát của nhà cung cấp. Thông báo ICO nói trên chưa kết luận vi phạm pháp luật.

### Case 2 — Getty Images kiện Stability AI: quyền sở hữu trí tuệ và watermark giả
- **Tổ chức / sản phẩm AI:** Stability AI — Stable Diffusion; bên kiện là Getty Images và các nguyên đơn liên quan.
- **Thời gian, địa điểm / bối cảnh:** Tranh chấp từ 2023; phán quyết ngày **04/11/2025** tại High Court, England and Wales.
- **AI được dùng để làm gì:** Tạo ảnh từ mô tả văn bản, cung cấp qua các phiên bản mô hình, DreamStudio và API.
- **Vấn đề hoặc sự kiện đáng chú ý:** Getty cáo buộc sử dụng ảnh để huấn luyện trái phép; một số ảnh đầu ra xuất hiện watermark Getty/iStock. Tòa xác định **một số vi phạm nhãn hiệu với phạm vi hẹp**, nhưng bác yêu cầu về vi phạm bản quyền gián tiếp. Getty đã rút yêu cầu liên quan trực tiếp đến huấn luyện do thiếu bằng chứng hoạt động này diễn ra tại Anh (High Court, 2025). [[judiciary.uk](https://www.judiciary.uk/wp-content/uploads/2025/11/Getty-Images-v-Stability-AI.pdf?utm_source=chatgpt.com)]
- **Số liệu có nguồn:** Stability thừa nhận trong tố tụng có khoảng **12,3 triệu “Visual Assets” trong LAION-2B-en**. Tuy nhiên, tòa **không xác định số tác phẩm thực tế được dùng để huấn luyện**; không được viết thành “12,3 triệu ảnh đã được chứng minh bị dùng trái phép” (High Court, 2025, đoạn 749–752). [[judiciary.uk](https://www.judiciary.uk/wp-content/uploads/2025/11/Getty-Images-v-Stability-AI.pdf?utm_source=chatgpt.com)]
- **Nguồn:**
  - **Hồ sơ chính:** [*Getty Images (US) Inc & Ors v Stability AI Ltd — [2025] EWHC 2863 (Ch)*](https://www.judiciary.uk/wp-content/uploads/2025/11/Getty-Images-v-Stability-AI.pdf?utm_source=chatgpt.com) — High Court, Justice Joanna Smith — 04/11/2025 — **205 trang PDF**; mục **F** về nhãn hiệu, **H** về bản quyền gián tiếp; đoạn **749–752** về số liệu, **757–758** về kết luận.
  - **Phân tích học thuật bổ sung:** [*Why Getty Images v Stability AI got secondary copyright infringement wrong*](https://academic.oup.com/jiplp/article/21/8/538/8721803?utm_source=chatgpt.com) — James Hall, *Journal of Intellectual Property Law & Practice* — công bố trực tuyến 29/06/2026 — **21(8), tr. 538–545**; phản biện cách tòa diễn giải bản quyền gián tiếp. [[Oxford Academic](https://academic.oup.com/jiplp/article/21/8/538/8721803?utm_source=chatgpt.com)]
- **Phân biệt bằng chứng và nhận định:**
  - **Bằng chứng:** phán quyết ghi nhận vi phạm nhãn hiệu trong một số trường hợp cụ thể.
  - **Nhận định của tôi:** watermark giả có thể làm người xem hiểu sai nguồn gốc ảnh. Phán quyết này không xác nhận mọi hoạt động huấn luyện AI đều hợp pháp; bài của Hall là lập luận học thuật, không phải phán quyết mới.

### Case 3 — LAION-5B: dữ liệu đầu vào chứa liên kết đến nội dung lạm dụng trẻ em
- **Tổ chức / sản phẩm AI:** LAION e.V. — tổ chức nghiên cứu phi lợi nhuận; bộ dữ liệu LAION-5B.
- **Thời gian, địa điểm / bối cảnh:** Phát hiện công bố tháng 12/2023; LAION báo cáo rút dữ liệu ngày **19/12/2023** và phát hành Re-LAION-5B ngày **30/08/2024**.
- **AI được dùng để làm gì:** LAION-5B cung cấp cặp văn bản–liên kết ảnh phục vụ huấn luyện mô hình hình ảnh, bao gồm các mô hình tạo ảnh. Đây là bộ dữ liệu metadata, không trực tiếp lưu toàn bộ ảnh được liên kết (Thiel, 2023). [[docs.house.gov](https://docs.house.gov/meetings/JU/JU08/20240306/116913/HHRG-118-JU08-20240306-SD005-U5.pdf?utm_source=chatgpt.com)]
- **Vấn đề hoặc sự kiện đáng chú ý:** Stanford phát hiện các mục dữ liệu nghi liên quan đến **CSAM — nội dung lạm dụng tình dục trẻ em**. LAION thừa nhận bộ lọc đã để lọt liên kết và phối hợp với các tổ chức bảo vệ trẻ em để làm sạch dữ liệu (LAION, 2024). [[LAION](https://laion.ai/blog/relaion-5b/?utm_source=chatgpt.com)]
- **Số liệu có nguồn:** LAION báo cáo loại bỏ **2.236 liên kết** bằng đối chiếu mã băm, bao gồm **1.008 liên kết** từ nghiên cứu Stanford. Phạm vi đối chiếu sử dụng danh sách đối tác đến **tháng 07/2024** (LAION, 2024). [[LAION](https://laion.ai/blog/relaion-5b/?utm_source=chatgpt.com)]
- **Nguồn:**
  - **Báo cáo điều tra chính:** [*Identifying and Eliminating CSAM in Generative ML Training Data and Models*](https://purl.stanford.edu/kh752sm9123?utm_source=chatgpt.com) — David Thiel, Stanford Internet Observatory — bản cập nhật **23/12/2023** — **21 trang PDF**; mục **2–4** về phương pháp/giới hạn/kết quả, **5–6** về khuyến nghị và đạo đức. [[Bản toàn văn lưu tại Hạ viện Mỹ](https://docs.house.gov/meetings/JU/JU08/20240306/116913/HHRG-118-JU08-20240306-SD005-U5.pdf?utm_source=chatgpt.com)]
  - **Báo cáo khắc phục:** [*Releasing Re-LAION-5B: transparent iteration on LAION-5B with additional safety fixes*](https://laion.ai/blog/relaion-5b/?utm_source=chatgpt.com) — LAION e.V. — 30/08/2024 — mục **Safety Revision**, **Results** và **Chronological protocol**.
- **Phân biệt bằng chứng và nhận định:**
  - **Bằng chứng:** 2.236 là số liên kết nghi chứa CSAM bị loại bỏ; một số có thể đã chết, không đồng nghĩa với 2.236 ảnh bất hợp pháp được xác minh.
  - **Nhận định của tôi:** kiểm soát an toàn phải bắt đầu từ dữ liệu huấn luyện. Các nguồn trên chưa chứng minh từng mục dữ liệu này đã được một mô hình cụ thể học hoặc tái tạo. [[LAION](https://laion.ai/blog/relaion-5b/?utm_source=chatgpt.com)]

```
