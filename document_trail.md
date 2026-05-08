# Document Trail — PapeBreak
**Date:** 08/05/2026

## Bảng đối chiếu 5 loại hồ sơ

| # | Loại | Status | Link/Path | Deadline build |
|---|------|--------|-----------|----------------|
| 1 | Nhật ký kiểm thử claim AI | ✗ | N/A | 15/05/2026 |
| 2 | Hồ sơ rà soát điều khoản vendor | ✗ | N/A | 20/05/2026 |
| 3 | Nhật ký giám sát giao dịch bất thường | ✗ | N/A | 01/06/2026 (Trước khi mở payment) |
| 4 | DPIA / CTIA | ✗ | N/A | 12/05/2026 |
| 5 | Phê duyệt nội dung marketing | ✓ | `marketing_claims_audit.md` | N/A (Đã có) |

## TOP 1 ưu tiên
**Loại:** #4 DPIA / CTIA (Hồ sơ đánh giá tác động xử lý & chuyển dữ liệu cá nhân ra nước ngoài).
**Lý do:** Khung luật PDPL đã chính thức có hiệu lực; PapeBreak đẩy trực tiếp các tài liệu nghiên cứu chưa công bố của sinh viên qua API nước ngoài (Gemini/Claude)[cite: 1] — nếu không có CTIA chứng minh bảo mật, hệ thống sẽ đối mặt với án phạt đình chỉ luồng dữ liệu ngay lập tức.

## Template build trong 1 tuần
### Người chịu trách nhiệm: Trịnh Uyên Chi - Founder / Product Manager
### Tần suất cập nhật: 1 lần ban đầu + Cập nhật khi thay đổi LLM vendor hoặc thay đổi luồng xử lý dữ liệu.
### Sample 3-5 dòng:
**HỒ SƠ ĐÁNH GIÁ TÁC ĐỘNG CHUYỂN DỮ LIỆU RA NƯỚC NGOÀI (CTIA)**
- **Loại dữ liệu chuyển đi:** Nội dung PDF học thuật (có thể chứa dữ liệu nghiên cứu chưa công bố), thông tin tài khoản (Email).
- **Bên nhận dữ liệu (Vendor):** Google LLC (Gemini 1.5 Pro API) / Anthropic (Claude 3.5 Sonnet API)[cite: 1].
- **Cơ sở pháp lý xử lý:** Sự đồng ý rõ ràng của chủ thể dữ liệu (người dùng phải tick chọn "Đồng ý chuyển dữ liệu để xử lý AI" tại màn hình upload PDF).
- **Biện pháp giảm thiểu rủi ro:** Áp dụng chính sách "Zero Data Retention" qua API, không dùng data sinh viên để train model[cite: 1].
- **Người phê duyệt:** [Chữ ký Founder - Trịnh Uyên Chi]