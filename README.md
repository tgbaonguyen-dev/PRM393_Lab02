# Expense Tracker - PRM393 Lab 2

Expense Tracker là ứng dụng di động hỗ trợ sinh viên sống xa nhà ghi nhận chi tiêu hằng ngày, theo dõi ngân sách theo danh mục và nhận biết sớm nguy cơ vượt hạn mức trong tháng.

## Persona

Nguyễn Minh, 21 tuổi, sinh viên năm ba đang thực tập bán thời gian, nhận tiền sinh hoạt theo tháng và thường quên ghi lại các khoản chi nhỏ. Chi tiết: [ux/persona.md](ux/persona.md).

## Ba luồng chính

1. Thêm một khoản chi và xem ngân sách được cập nhật.
2. Chỉnh sửa hoặc xóa giao dịch, có xác nhận và hoàn tác.
3. Tạo ngân sách, theo dõi cảnh báo và xuất báo cáo PDF.

Chi tiết kiến trúc thông tin và sơ đồ: [ux/user-flow.md](ux/user-flow.md).

## Deliverables

| Deliverable | Vị trí |
| --- | --- |
| Mô tả tổng quan ứng dụng | [docs/application-description.md](docs/application-description.md) |
| Yêu cầu Lab 2 đã chuẩn hóa | [requirements/LAB2_REQUIREMENTS.md](requirements/LAB2_REQUIREMENTS.md) |
| Phạm vi sản phẩm | [requirements/EXPENSE_TRACKER_REQUIREMENTS.md](requirements/EXPENSE_TRACKER_REQUIREMENTS.md) |
| Persona và problem statement | [ux/persona.md](ux/persona.md) |
| Information architecture và user flow | [ux/user-flow.md](ux/user-flow.md) |
| Định hướng thiết kế | [design/DESIGN.md](design/DESIGN.md) |
| Đặc tả màn hình | [design/screen-spec.md](design/screen-spec.md) |
| Quyết định thiết kế | [design/design-decisions.md](design/design-decisions.md) |
| Nhật ký thiết kế với AI | [ai/ai-design-log.md](ai/ai-design-log.md) |
| Flutter handoff | [handoff/flutter-handoff.md](handoff/flutter-handoff.md) |
| Kế hoạch phân chia công việc nhóm | [TEAM_WORK_DIVISION.md](TEAM_WORK_DIVISION.md) |
| Ảnh kết quả Google Stitch | `assets/stitch/` |
| Ảnh export từ Figma | `assets/figma/` |

## Figma

- Link: [PRM393 Lab 02 - Expense Tracker](https://www.figma.com/design/rz0luZHIOihvPCvL6UptPl/PRM393_Lab02_ExpenseTracker?node-id=1-2&t=h0JKZKs9SUXr4RZX-1)
- Frame Final UI: `360 x 800 dp`
- Kiểm tra responsive: `360 dp` và `412 dp`
- Pages bắt buộc: `01 User Flow`, `02 Wireframe`, `03 Final UI`, `04 Design System`, `05 Components`, `06 Prototype`

## Google Stitch

- Link: [Expense Tracker project](https://stitch.withgoogle.com/projects/10313498934502515057?pli=1)
- Bằng chứng các phiên bản và vòng lặp: [`assets/stitch/`](assets/stitch/)

## Công cụ AI

| Công cụ | Mục đích | Trạng thái |
| --- | --- | --- |
| Google Stitch | Tạo UI ban đầu và 3 vòng tinh chỉnh | Đã thực hiện |
| ChatGPT/Codex | Phân tích yêu cầu, phản biện UX và hỗ trợ tài liệu | Đang sử dụng |

Mọi prompt, kết quả và quyết định phải được ghi nguyên văn trong [ai/ai-design-log.md](ai/ai-design-log.md).

## Quy tắc phạm vi

- Lab 2 chỉ thiết kế, không viết Flutter.
- Không triển khai OCR hóa đơn, đồng bộ ngân hàng, mạng xã hội, AI coach, quản lý nợ hoặc đầu tư.
- Không tuyên bố bằng chứng AI, kiểm thử hay accessibility nếu chưa thực hiện và lưu bằng chứng thật.
