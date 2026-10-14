# Thành viên 3 — Ngân sách, báo cáo, hồ sơ

Nhánh làm việc: `dev`. Phạm vi lấy từ mục **Thành viên 3** trong `TEAM_WORK_DIVISION.md`.

## Kết quả Figma — 13/10/2026

Quyền sửa đã được cấp. Đã dựng 6 màn hình chính cùng các state bằng instance từ `05 Components` trên `03 Final UI` (frame IDs `189:536` đến `189:552`), dùng Auto Layout và token chung. HM/TX/AU/NT trong prototype được clone từ màn hình của thành viên 2; không thay đổi frame nguồn của họ.

Đã gắn 3 Flow Starting Points trên `06 Prototype`:

- Flow 1 — `192:106`: Home → form thêm → filled → submitting → chi tiết → Home có tổng chi cập nhật. Chạm trường nhập mô phỏng bộ giá trị mẫu, không phải nhập văn bản trực tiếp.
- Flow 2 — `192:652`: danh sách → chi tiết → confirmation overlay → danh sách với Snackbar Undo → phục hồi.
- Flow 3 — `192:1012`: ngân sách → chi tiết → điều chỉnh hạn mức → 72% → phân tích → xuất PDF → loading → ready → xem trước PDF.

Đã nối Retry, Cancel, Back, tab bar và xác nhận đăng xuất. Export mở từ Hồ sơ dùng các frame riêng để giữ đúng nguồn khi Back. PDF là bản xem trước trong prototype; không tạo file báo cáo thật.

Kiểm tra cấu trúc: 36 frame, 141 liên kết, 3 chuyển cảnh tự động, không có đích ngoài page hoặc frame thiếu lối ra; font Inter và frame màn hình 360 × 800. Xem `prototype-audit.json`. Kiểm tra này không thay thế việc chạy thử bằng chuột trong Presentation; chưa kiểm tra responsive 412 dp hoặc đo contrast toàn bộ màn hình.

- [Mở page Prototype](https://www.figma.com/design/rz0luZHIOihvPCvL6UptPl/PRM393_Lab02_ExpenseTracker?node-id=1-6)
- [Chạy Flow 3](https://www.figma.com/proto/rz0luZHIOihvPCvL6UptPl/PRM393_Lab02_ExpenseTracker?page-id=1-6&node-id=192-1012&starting-point-node-id=192%3A1012)
- Ảnh xuất thực tế Figma: `../../assets/figma/member-3/prototype-ready.png`.

Các ghi chú bên dưới là lịch sử trước khi được cấp quyền sửa; trạng thái hiện tại nằm ở mục này.

- Project Stitch gốc của nhóm: https://stitch.withgoogle.com/projects/10313498934502515057
- Bản Remix để dựng phần 3: https://stitch.withgoogle.com/projects/12845800747539664021
- File Figma của nhóm: https://www.figma.com/design/rz0luZHIOihvPCvL6UptPl/PRM393_Lab02_ExpenseTracker

## Tệp chuẩn bị

| Tệp | Nội dung |
| --- | --- |
| `screen-content.json` | Nội dung, số liệu mẫu và hành động của 6 màn hình |
| `stitch-prompts.md` | Prompt chi tiết chuẩn bị cho màn hình và các state |
| `render-preview.mjs` | Tạo bản vẽ SVG cục bộ để rà bố cục trước khi dựng trên dịch vụ |
| `../../assets/member-3/index.html` | Gallery bản vẽ cục bộ (không phải export Stitch/Figma) |
| `../../assets/member-3/overview.png` | Tổng quan sáu bản vẽ cục bộ |

Chạy lại bản vẽ cục bộ bằng `node design/member-3/render-preview.mjs`.

## Trạng thái thực hiện

- Đã đọc DESIGN, screen-spec, user-flow và Flutter handoff.
- Đã kiểm tra thư viện Figma `05 Components` bằng chế độ xem; thư viện hiện có component cho ngân sách, báo cáo và hồ sơ.
- Đã xác nhận 6 màn hình và các state của thành viên 2 có trên `03 Final UI`.
- Tài khoản Figma kết nối thành công, nhưng bị từ chối quyền sửa file nhóm. Chưa tạo instance hoặc nối prototype trong Figma.
- Đã đăng nhập Stitch và Remix project gốc theo chức năng của Stitch vì project gốc chỉ có quyền xem.
- Đã tạo 6 màn hình chính và 8 biến thể trên bản Remix Stitch; đã thấy các frame trên canvas. Không dựa vào lời xác nhận của AI để đánh dấu đạt chất lượng.
- Kiểm tra trực tiếp phát hiện một số tiêu đề bị sao chép từ màn hình giao dịch và frame warning có kích thước 390 × 1290. Đã gửi lượt sửa thực tế, bổ sung BD-02 sau cập nhật, BD-03 lỗi nhập liệu và trình xem PDF.
- Lượt sửa đã tạo thêm 3 frame: BD-02 sau cập nhật 72%, BD-03 lỗi nhập liệu và trình xem PDF. Đã thấy ba frame bổ sung trên canvas; một số frame vẫn mang nhãn `Generating Screen...` dù nội dung đã hiển thị.
- Tiêu đề EX-01 đã đổi thành Xuất báo cáo trên canvas. Tuy nhiên, Properties của BD-01 Warning vẫn ghi 390 × 1290 sau lượt sửa; chưa đạt kích thước chuẩn 360 × 800. Không xác nhận responsive 412 hoặc accessibility chỉ từ lời AI.
- Stitch đã đính chính rằng lượt tạo màn hình không gán hotspot giữa các artboard. Chưa xác nhận có prototype tương tác; 3 Flow Starting Points trong Figma vẫn còn thiếu.
- Export ZIP hiện thông báo `Downloaded screen` nhưng chưa lấy được đường dẫn tải trong môi trường điều khiển. Chưa lưu bản export Stitch vào repo; các ảnh trong assets/member-3 chỉ là bản vẽ cục bộ.
- Bản vẽ cục bộ có 6 màn hình chính và 10 biến thể. Không dùng các bản vẽ này để tuyên bố đã có Auto Layout, component instance, Figma prototype hoặc test responsive.

## Đối chiếu số liệu mẫu

- BD-01 mặc định: chi 4.050.000 / hạn mức 6.000.000 đ, còn 1.950.000 đ.
- BD-01 warning: chi 4.650.000 đ, còn 1.350.000 đ; Ăn uống đạt 90%.
- BD-01 exceeded: chi 5.050.000 đ, còn 950.000 đ tổng tháng; riêng Ăn uống đạt 110%, vượt 200.000 đ. Không đánh đồng vượt danh mục với vượt tổng tháng.
- BD-02: ba giao dịch 700.000 + 500.000 + 600.000 = 1.800.000 đ.
- IN-01: 2.400.000 + 1.800.000 + 450.000 = 4.650.000 đ; tỷ trọng làm tròn 51,6% + 38,7% + 9,7% = 100%.
- BD-03 tạo mới dùng Học tập để tránh trùng danh mục/tháng; chế độ sửa dùng Ăn uống.

## Các phần còn cần thực hiện trên Figma

1. Dựng `BD-01`, `BD-02`, `BD-03`, `IN-01`, `EX-01`, `ST-01` trên `03 Final UI` bằng instance từ `05 Components`, bind token, giữ Auto Layout.
2. Đặt warning/exceeded của BD-01 và empty của IN-01 cạnh frame gốc; thêm processing/ready của EX-01 phục vụ prototype.
3. Trên `06 Prototype`, dùng frame HM/TX của thành viên 2 và frame ngân sách/báo cáo để thiết lập 3 Flow Starting Points, dialog overlay, Undo và loading → ready.
4. Kiểm tra Back về đúng nguồn, không có ngõ cụt, chiều rộng 360/412 dp và contrast/touch target thực tế.

Không sửa tài liệu AI/design system hoặc vẽ thay màn hình thuộc phạm vi thành viên 1/2.
