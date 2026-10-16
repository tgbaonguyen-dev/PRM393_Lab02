# Expense Tracker - PRM323 Lab 2

Expense Tracker là ứng dụng di động hỗ trợ sinh viên sống xa nhà ghi nhận chi tiêu hằng ngày, theo dõi ngân sách theo danh mục và nhận biết sớm nguy cơ vượt hạn mức trong tháng.

## Tổng quan sản phẩm

Sinh viên sống xa gia đình thường nhận tiền sinh hoạt theo tháng nhưng phát sinh nhiều khoản chi nhỏ và dễ quên ghi lại. Khi dữ liệu không được cập nhật, họ khó biết đã chi vào đâu, còn bao nhiêu và khoản chi mới ảnh hưởng thế nào đến ngân sách.

Expense Tracker giải quyết vấn đề này bằng vòng lặp ngắn:

> Ghi khoản chi → ngân sách cập nhật → hiểu xu hướng → điều chỉnh hành vi → xuất báo cáo.

Sản phẩm ưu tiên thao tác nhanh, thông tin dễ hiểu, khả năng phục hồi khi có lỗi và ngôn ngữ không phán xét. Các chức năng chính gồm đăng nhập, Home Dashboard, quản lý giao dịch, ngân sách theo danh mục, Insights, cảnh báo và báo cáo PDF. Thiết kế gồm 12 màn hình, được chuẩn bị để triển khai bằng Flutter và Firebase ở Lab 3.

### Mục tiêu và tiêu chí thành công

- Ghi một khoản chi và thấy ngân sách cập nhật trong dưới 20 giây.
- Xác định danh mục cần chú ý trong dưới 10 giây từ Home.
- Hoàn thành ba user flow từ đầu đến cuối, có nhánh thay thế và phục hồi lỗi.
- Giữ dữ liệu đã nhập khi validation hoặc lỗi mạng; xác nhận và cho phép Undo khi xóa.
- Đáp ứng body text tối thiểu 14 sp, touch target 48 × 48 dp, không truyền đạt trạng thái chỉ bằng màu và kiểm tra ở 360/412 dp.

### Ngoài phạm vi

OCR hóa đơn, đồng bộ ngân hàng/ví điện tử, thanh toán, chi phí nhóm, mạng xã hội, AI tư vấn tài chính, đầu tư, khoản vay, subscription, iOS và web admin không thuộc phạm vi Lab 2.

## Persona

Ba **Proto-Persona chưa xác thực**, phân biệt theo hành vi và đối chiếu với chức năng hiện có:

- **P01 · Nguyễn Minh — Primary:** ghi khoản chi ngay trong phiên ngắn.
- **P02 · Trần Thảo — Secondary:** chủ động hiểu và kiểm soát hạn mức.
- **P03 · Lê Huy — Secondary:** rà soát, sửa sai và tổng hợp cuối kỳ.

Chi tiết đủ 12 trường: [ux/persona.md](ux/persona.md). Tên/tuổi/tiểu sử chỉ minh họa; không phải kết quả phỏng vấn. Ba persona không tạo role hoặc tính năng mới; một người thật có thể thể hiện nhiều kiểu hành vi và nghiên cứu có thể dẫn đến gộp persona.

## Ba luồng chính

1. Thêm một khoản chi và xem ngân sách được cập nhật.
2. Chỉnh sửa hoặc xóa giao dịch, có xác nhận và hoàn tác.
3. Tạo ngân sách, theo dõi cảnh báo và xuất báo cáo PDF.

Chi tiết kiến trúc thông tin và sơ đồ: [ux/user-flow.md](ux/user-flow.md).

## Deliverables

| Deliverable | Vị trí |
| --- | --- |
| Mô tả tổng quan ứng dụng | [README — Tổng quan sản phẩm](#tổng-quan-sản-phẩm) |
| Yêu cầu Lab 2 đã chuẩn hóa | [requirements/LAB2_REQUIREMENTS.md](requirements/LAB2_REQUIREMENTS.md) |
| Phạm vi sản phẩm | [requirements/EXPENSE_TRACKER_REQUIREMENTS.md](requirements/EXPENSE_TRACKER_REQUIREMENTS.md) |
| Persona và problem statement | [ux/persona.md](ux/persona.md) |
| User/Stakeholder Map, board giả định, coverage và backlog | [ux/discovery-and-evidence.md](ux/discovery-and-evidence.md) |
| Scenarios, Persona → Need → UI → Test | [ux/scenarios-and-tests.md](ux/scenarios-and-tests.md) |
| Research plan, evidence template và self-review | [ux/research-plan-and-review.md](ux/research-plan-and-review.md) |
| Information architecture và user flow | [ux/user-flow.md](ux/user-flow.md) |
| Định hướng thiết kế | [design/DESIGN.md](design/DESIGN.md) |
| Đặc tả màn hình | [design/screen-spec.md](design/screen-spec.md) |
| Quyết định thiết kế | [design/design-decisions.md](design/design-decisions.md) |
| Nhật ký thiết kế với AI | [ai/ai-design-log.md](ai/ai-design-log.md) |
| Flutter handoff | [handoff/flutter-handoff.md](handoff/flutter-handoff.md) |
| Kế hoạch phân chia công việc nhóm | [TEAM_WORK_DIVISION.md](TEAM_WORK_DIVISION.md) |
| Ảnh kết quả Google Stitch | `assets/stitch/` |
| Ảnh export từ Figma | `assets/figma/` |

## Quy ước nộp bài và tài nguyên

- Theo PDF PRM323 Lab 2, tên GitHub repository cần là `prm323-lab2-<student-id>`; nếu làm nhóm, xác nhận hậu tố với giảng viên. Repository hiện tại chưa được đổi tên vì chưa có mã nộp bài được xác nhận.
- `presentation/` là tài liệu thuyết trình riêng, không thuộc cấu trúc bắt buộc trong PDF và không cần đặt lại vào repository. Bằng chứng cần chấm vẫn phải có trong repository/Figma, không chỉ nằm trong slide.
- PNG Final UI: `SCREEN-ID-short-name-state.png`, giữ ID viết hoa, phần còn lại dùng chữ thường và dấu gạch nối; xem [danh mục ảnh](assets/figma/README.md).
- `assets/figma/component-exports/` và `assets/figma/variable-exports/` chứa export thư viện và token.
- Bằng chứng prototype xuất từ Figma nằm tại `assets/figma/prototype-evidence/`; các workspace và script tạo trung gian không nằm trong gói nộp.
- [Kiểm tra contrast token độc lập với slide](design/accessibility-evidence.md).

## Figma project

- Link: [Expense Tracker — Figma](https://www.figma.com/design/rz0luZHIOihvPCvL6UptPl/PRM393_Lab02_ExpenseTracker?node-id=1-2&t=h0JKZKs9SUXr4RZX-1)
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
