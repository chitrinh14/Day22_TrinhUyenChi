## 1. Thông tin chung

* **Dự án:** PapeBreak
* **Phiên bản:** v2.0 (Compliance Audit)
* **Người thực hiện:** Trịnh Uyên Chi (BA/PM)
* **Ngày lập:** 08/05/2026

## 2. Danh sách 7 Vi phạm cốt lõi (Theo rà soát của AI)

### NHÓM 1: VI PHẠM VỀ MARKETING CLAIM (PATTERN: VỤ KẸO KERA - ĐIỀU 198 BLHS)

Trong vụ Kera 11/2025, 3 KOL đi tù vì quảng cáo sản phẩm có công dụng "tuyệt đối" nhưng thực tế không đạt được. PapeBreak đang giẫm đúng vết xe đổ này.

**VI PHẠM 1: Cam kết "Triệt tiêu hoàn toàn" sai sự thật về mặt kỹ thuật**

* **Luật áp dụng:** Bộ luật Hình sự VN
* **Điều:** Điều 198, Khoản 1 (Tội lừa dối khách hàng)
* **Bằng chứng trong sản phẩm:** Khẳng định sản phẩm giúp "triệt tiêu hoàn toàn sự "ảo giác" và đảm bảo chất lượng khoa học." Tuy nhiên, ở phần Success Metrics lại tự thừa nhận "Tỷ lệ Báo lỗi/Ảo giác duy trì ở mức < 5%."


* **Pattern khớp với:** Vụ kẹo Kera (Quảng cáo "khỏi bệnh 100%" nhưng hồ sơ nội bộ chấp nhận tỷ lệ thất bại 5%).
* **Hành động sửa:** Gỡ ngay lập tức cụm từ "triệt tiêu hoàn toàn". Thay bằng "giảm thiểu rủi ro ảo giác thông qua cơ chế human-in-the-loop".
* **Deadline:** Trong vòng 48 giờ trước khi publish bất kỳ tài liệu marketing nào.

**VI PHẠM 2: Tuyên bố "Tuyệt đối không chấp nhận" gây hiểu lầm nghiêm trọng**

* **Luật áp dụng:** Bộ luật Hình sự VN
* **Điều:** Điều 198, Khoản 1 (Tội lừa dối khách hàng)
* **Bằng chứng trong sản phẩm:** "Tuyệt đối không chấp nhận Hallucination. Thà AI trả lời "Không biết" còn hơn tự bịa ra một số liệu không có trong bài." Thực tế, không một hệ thống GenAI/RAG nào hiện nay cam kết được mức 0% Hallucination.


* **Pattern khớp với:** Vụ kẹo Kera (Tuyên truyền thông điệp sai lệch bản chất khoa học để tạo niềm tin giả tạo).
* **Hành động sửa:** Bổ sung Disclaimer bắt buộc trên UI: "AI có thể tạo ra thông tin không chính xác. Người dùng bắt buộc phải đối chiếu bản gốc."
* **Deadline:** Xong trước khi launch bản Closed Beta.

**VI PHẠM 3: Cam kết "Chuẩn xác" nhưng đổ lỗi cho thiết bị đầu vào**

* **Luật áp dụng:** Bộ luật Hình sự VN (Điều 198) & EU AI Act (Điều khoản về Minh bạch)
* **Điều:** Điều 198 BLHS; Article 50 EU AI Act
* **Bằng chứng trong sản phẩm:** Mở đầu cam kết "trích xuất chuẩn xác dữ liệu", nhưng phần Constraints lại lấp liếm: "Hệ thống có thể không hoạt động chính xác với các file PDF được scan bằng máy photocopy đời cũ, file mờ chữ..."


* **Pattern khớp với:** Vụ kẹo Kera (Che giấu các điều kiện ngoại trừ (constraints) để lừa khách hàng mua/sử dụng).
* **Hành động sửa:** Đưa Constraints thành một popup "Điều khoản sử dụng" (Terms of Service) rõ ràng ngay màn hình Upload PDF. Yêu cầu user tick đồng ý.
* **Deadline:** Implement trong Sprint tiếp theo (Tối đa 7 ngày).

---

### NHÓM 2: VI PHẠM VỀ DỮ LIỆU CÁ NHÂN (PATTERN: VỤ RÒ RỈ CIC - PDPL)

Vụ rò rỉ CIC tháng 9/2025 đã cho thấy việc xử lý dữ liệu không khai báo rõ ràng bị phạt 10x doanh thu. Data Flow của PapeBreak đang lừa dối người dùng.

**VI PHẠM 4: Chuyển dữ liệu cá nhân xuyên biên giới trái phép**

* **Luật áp dụng:** Luật BVDLCN (PDPL) 91/2025/QH15
* **Điều:** Điều 30 (Chuyển dữ liệu cá nhân ra nước ngoài)
* **Bằng chứng trong sản phẩm:** Cấu trúc sử dụng "Các LLM hỗ trợ Vision mạnh như Gemini 1.5 Pro hoặc Claude 3.5 Sonnet" để xử lý "File PDF học thuật do người dùng tự upload." Các API này đẩy dữ liệu sang server US. Trong PDF học thuật luôn chứa Dữ liệu cá nhân (Tên tác giả, email, thông tin định danh nghiên cứu).


* **Pattern khớp với:** Vụ rò rỉ CIC (Đẩy data user qua 3rd-party API server nước ngoài mà không xin phép).
* **Hành động sửa:** Bổ sung luồng xin Consent (Đồng ý) việc chuyển dữ liệu sang máy chủ nước ngoài (Google/Anthropic) trước khi gọi API. Làm báo cáo Đánh giá tác động chuyển dữ liệu (DPIA).
* **Deadline:** 72 giờ trước khi API key được kích hoạt trên production.

**VI PHẠM 5: Lừa dối về việc "Không lưu trữ dữ liệu"**

* **Luật áp dụng:** Luật BVDLCN (PDPL) 91/2025/QH15
* **Điều:** Điều 8 & Điều 21 (Quy định về Xử lý dữ liệu và Minh bạch)
* **Bằng chứng trong sản phẩm:** Tuyên bố "(hệ thống không lưu lại data để train model nhằm bảo mật các nghiên cứu chưa công bố)". Về mặt kỹ thuật RAG, bạn BẮT BUỘC phải "áp dụng kỹ thuật Sliding Window kết hợp Overlap chunking" và lưu trữ các Vector Embeddings trong một Vector Database để truy xuất. Dữ liệu ĐÃ bị lưu trữ, dù là dưới dạng vector.


* **Pattern khớp với:** Vụ rò rỉ CIC (Tuyên bố "xóa data sau khi dùng" nhưng thực chất vẫn lưu cache/vector).
* **Hành động sửa:** Sửa lại Privacy Policy: Cần nêu rõ "Hệ thống có lưu trữ dữ liệu dưới dạng mã hóa (Vector Embeddings) trong thời gian session hoạt động và sẽ tự động xóa sau [X] giờ."
* **Deadline:** Cập nhật Document trong 3 ngày làm việc.

---

### NHÓM 3: VI PHẠM VỀ PHÂN LOẠI RỦI RO AI

**VI PHẠM 6: Bỏ qua Đánh giá rủi ro cho AI tạo sinh trong Giáo dục/Học thuật**

* **Luật áp dụng:** Luật AI Việt Nam 134/2025/QH15 & EU AI Act
* **Điều:** Điều 9 (Phân loại rủi ro hệ thống AI)
* **Bằng chứng trong sản phẩm:** Mục tiêu trong AI Critique Log (phần bị Reject) lộ rõ ý định: "Mục tiêu cuối cùng vẫn có tính năng viết báo cáo giùm người dùng... và công cụ cũng phải trích dẫn giùm người dùng luôn."


* **Pattern khớp với:** Trốn tránh khai báo. Theo EU AI Act và Luật AI VN mới, các công cụ AI can thiệp vào kết quả giáo dục, điểm số hoặc tạo nội dung khoa học có nguy cơ bị xếp vào nhóm "Rủi ro cao" (High-risk) do khả năng tạo ra nghiên cứu rác/đạo văn.
* **Hành động sửa:** Tạm thời phong tỏa tính năng "viết báo cáo giùm" và "tự động trích dẫn" khỏi roadmap. Phải nộp Hồ sơ Đánh giá Rủi ro AI lên Cục An toàn Thông tin trước khi code tính năng này.
* **Deadline:** Phải nộp hồ sơ xin phép 30 ngày trước khi mở khóa tính năng này cho user.

---

### NHÓM 4: VI PHẠM VỀ VENDOR/PAYMENT (PATTERN: VỤ MR PIPS - ĐIỀU 324 BLHS)

Vụ Shark Bình (Mr Pips) 2/2026 bị đề nghị truy tố vì hệ thống thanh toán tiếp tay cho rửa tiền bằng cách lách luật payment gateway.

**VI PHẠM 7: Rủi ro lạm dụng API và thanh toán ẩn danh (Cửa rửa tiền)**

* **Luật áp dụng:** Bộ luật Hình sự VN
* **Điều:** Điều 324 (Tội rửa tiền)
* **Bằng chứng trong sản phẩm:** Bạn xác định "sẵn sàng trả mức phí cao để bù đắp chi phí API Multimodal đắt đỏ" và MVP "cần có rào cản để không "đốt" sạch ngân sách API". Nếu bạn thu khoản "phí cao" này qua các cổng thanh toán crypto, thẻ cào, hoặc nhận tiền từ thẻ tín dụng đánh cắp (CC chùa) của sinh viên quốc tế mà không có KYC (Định danh khách hàng), bạn đang biến PapeBreak thành một cỗ máy rửa tiền thành API credits.


* **Pattern khớp với:** Vụ Mr Pips (Dùng nền tảng công nghệ làm bình phong để nạp tiền bẩn -> chuyển hóa thành dịch vụ số/API calls).
* **Hành động sửa:** Tích hợp eKYC ngay khi user nạp tiền mua token. Chỉ nhận thanh toán qua các cổng Payment Gateway được NHNN cấp phép (VNPay, MoMo, Napas). Cấm nhận Crypto.
* **Deadline:** Phải hoàn thiện API Payment nội địa có KYC trước khi thu đồng doanh thu đầu tiên.

## 3. Bảng đối chiếu Workshop (Gap Analysis)

| Loại vi phạm | Workshop liên quan | Đối chiếu thực tế |
| --- | --- | --- |
| **Marketing thổi phồng** | WS1 — Rà soát claim | AI phát hiện điểm mâu thuẫn cực kỳ tinh vi: Bạn tuyên bố "Triệt tiêu" nhưng lại ghi Success Metric là "< 5%". Đây là bằng chứng tự đối đầu (self-incrimination). |
| **Tầng rủi ro AI** | WS2 — Phân loại | AI đánh giá cao hơn một bậc (High-risk) vì can thiệp vào kết quả học tập/nghiên cứu, đòi hỏi hồ sơ lên Cục ATTT. |
| **Dữ liệu cá nhân** | Tech stack & Flow | Phát hiện lỗi "chuyển dữ liệu xuyên biên giới" (Điều 30 PDPL) do dùng API ngoại, điều mà PRD thường chỉ ghi là "gọi API". |
| **Thanh toán/Rửa tiền** | WS3 — Vendor | Cảnh báo về việc biến API credits thành công cụ "rửa" tiền bẩn nếu không có eKYC. |

## 4. Kế hoạch khắc phục (TOP 5 Ưu tiên)

### TOP 1: Tội lừa dối khách hàng (Claim "Triệt tiêu hoàn toàn" ảo giác)

* **Hành động 1:** Sửa toàn bộ Landing Page và Pitch Deck: Thay "Triệt tiêu (Eliminate)" bằng "Kiểm soát và Giảm thiểu (Mitigate)".
* **Hành động 2:** Công khai chỉ số "Hallucination Rate" trong phần giới thiệu kỹ thuật để thể hiện sự minh bạch (Transparency).
* **Hành động 3:** Cài đặt "Confidence Score" (Mức độ tự tin) hiển thị cạnh mỗi câu trả lời của AI để user tự đánh giá.

### TOP 2: Vi phạm chuyển dữ liệu ra nước ngoài (Dùng API Gemini/Claude)

* **Hành động 1:** Thêm checkbox "Consent" (Đồng ý) riêng biệt khi user upload file, nêu rõ: "Dữ liệu sẽ được xử lý bởi đối tác AI (Google/Anthropic) tại máy chủ nước ngoài".
* **Hành động 2:** Thiết lập quy trình **Anonymization** (Ẩn danh hóa): Tự động quét và che mờ tên, email, số điện thoại trong PDF trước khi đẩy lên API.
* **Hành động 3:** Soạn thảo văn bản "Đánh giá tác động xử lý dữ liệu cá nhân" (DPIA) lưu trữ nội bộ để đối phó khi có thanh tra.

### TOP 3: Lừa dối về việc lưu trữ (Vector Database vs "Không lưu data")

* **Hành động 1:** Sửa lại cam kết bảo mật thành: "Không sử dụng dữ liệu người dùng để huấn luyện lại model (No training usage), nhưng có lưu trữ tạm thời dưới dạng Vector để phục vụ truy xuất".
* **Hành động 2:** Cấu hình chính sách **TTL (Time-to-Live)** cho Vector DB: Tự động xóa vĩnh viễn vector embedding sau khi session kết thúc hoặc sau 24h.
* **Hành động 3:** Thêm nút "Xóa toàn bộ dữ liệu dự án" (Hard Delete) cho người dùng chủ động thực hiện.

### TOP 4: Rủi ro tiếp tay rửa tiền (Thanh toán phí API cao)

* **Hành động 1:** Loại bỏ hoàn toàn ý định nhận Crypto hoặc nạp thẻ cào. Chỉ tích hợp cổng thanh toán có liên kết ngân hàng (VNPay/ZaloPay).
* **Hành động 2:** Áp dụng **Tiered Verification**: Nạp dưới 500k chỉ cần số điện thoại, nạp trên 500k bắt buộc liên kết tài khoản ngân hàng chính chủ (eKYC nhẹ).
* **Hành động 3:** Giới hạn hạn mức (Quota) nạp tiền theo ngày để ngăn chặn các giao dịch bất thường với số lượng lớn.

### TOP 5: Rủi ro AI bậc cao trong giáo dục (Viết báo cáo hộ)

* **Hành động 1:** Giới hạn tính năng ở mức "Gợi ý cấu trúc" và "Trích xuất thông tin", không cho phép AI viết trọn vẹn 100% nội dung báo cáo.
* **Hành động 2:** Chèn Watermark ngầm hoặc Metadata vào các đoạn văn bản do AI tạo ra để các công cụ check đạo văn có thể nhận diện.
* **Hành động 3:** Thêm mục "Hướng dẫn sử dụng có đạo đức" (Ethical AI Use) vào bộ quy tắc ứng xử của người dùng trên nền tảng.

## 5. Kết luận & Cam kết

* Xác nhận các mốc thời gian (Deadline) hoàn thành cho từng hạng mục (ví dụ: 48h cho Marketing, 7 ngày cho Dev).
* Lưu ý về việc nộp hồ sơ xin phép Cục An toàn thông tin.