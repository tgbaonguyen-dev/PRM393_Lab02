# Design Decisions

Chỉ ghi tối đa 10 quyết định quan trọng. Cập nhật trạng thái bằng bằng chứng Figma sau khi thực hiện.

## Decisions

| # | Quyết định | Lý do | Cơ sở |
| --- | --- | --- | --- |
| 1 | Dùng bốn tab Home, Giao dịch, Ngân sách, Hồ sơ | Các khu vực chính truy cập trong một chạm, phù hợp phiên dùng ngắn | Persona; recognition rather than recall |
| 2 | Add Expense là FAB/primary action, không phải tab | Đây là hành động thường xuyên nhưng là task tạm thời, không phải destination | Visual hierarchy; Material navigation pattern |
| 3 | Giữ form khoản chi trên một màn hình | Giảm bước và hỗ trợ mục tiêu hoàn thành dưới 20 giây | Success criterion |
| 4 | Hiển thị lỗi ngay dưới field và giữ dữ liệu | Người dùng có thể sửa lỗi mà không phải nhập lại | Error recovery; persona |
| 5 | Xóa dùng confirmation và Snackbar Undo | Ngăn lỗi nhưng vẫn cho phép phục hồi nhanh | Error prevention; user control |
| 6 | Budget state dùng icon, text và màu | Người dùng không phụ thuộc khả năng phân biệt màu | Accessibility |
| 7 | Cảnh báo dùng ngôn ngữ trung tính | Tránh tạo cảm giác tội lỗi và tăng khả năng tiếp tục sử dụng | Persona; product tone |
| 8 | Chart luôn có text summary và drill-down | Biểu đồ không phải nguồn thông tin duy nhất | Accessibility; visibility of system status |
| 9 | Thiết kế Login và Profile ngay từ Lab 2 | Lab 3 bắt buộc Google Sign-In và profile; giảm design change về sau | Implementation constraint |
| 10 | Không đưa OCR và bank sync vào MVP | Không bắt buộc trong Lab 3 và tạo thêm rủi ro dịch vụ ngoài | Scope và thời gian |

## Accessibility checklist

Không đánh dấu đạt nếu chưa kiểm tra bằng Figma/plugin hoặc công cụ contrast thực tế.

| Hạng mục | Mục tiêu | Kết quả | Bằng chứng |
| --- | --- | --- | --- |
| Text contrast | 4.5:1 | Đã tính 6 cặp token khai báo: 5 đạt, 1 chưa đạt; chưa audit frame | [Bảng đo token](accessibility-evidence.md) |
| Large text/UI contrast | 3:1 | Chưa kiểm tra | `[BỔ SUNG]` |
| Touch target | Tối thiểu 48 x 48 dp | Chưa kiểm tra | `[BỔ SUNG]` |
| Body text | Tối thiểu 14 sp | Đã quy định, chưa kiểm tra frame | `[BỔ SUNG]` |
| Color independence | Icon + text + color | Đã quy định, chưa kiểm tra frame | `[BỔ SUNG]` |
| Width 360 dp | Không overflow/clipping | Chưa kiểm tra | `[BỔ SUNG]` |
| Width 412 dp | Layout giãn đúng | Chưa kiểm tra | `[BỔ SUNG]` |
| Large text | Không mất nội dung quan trọng | Chưa kiểm tra | `[BỔ SUNG]` |

## Responsive notes

- 360 dp: dùng padding 16 dp; amount có thể wrap trước action phụ.
- 412 dp: giữ một cột và tăng khoảng trống trong card, không tăng font tùy ý.
- Từ 600 dp: giới hạn content width 600 dp và căn giữa.

## Bổ sung kiểm chứng token — 2026-10-15

Các tỷ lệ trong [bằng chứng contrast](accessibility-evidence.md) được tính từ màu khai báo trong `design/DESIGN.md` theo relative luminance sRGB vào ngày 2026-10-16. Kết quả không đọc binding/layer thực tế trong Figma và không suy ra responsive từ ảnh chụp.

- CTA trắng trên primary: **6.32:1**, đạt mục tiêu chữ thường.
- Body trên surface trắng: **16.50:1**, đạt.
- Chữ phụ trên surface trắng: **6.59:1**, đạt.
- Warning `#9A5B00` trên `#FFE2B8`: **4.35:1**, chưa đạt mục tiêu 4.5:1 cho chữ thường; cần chỉnh token và kiểm tra lại tại source.
- Error trên errorContainer: **5.00:1**, đạt.
- onPrimaryContainer trên primaryContainer: **10.65:1**, đạt.

Chưa chỉnh source Figma/prototype. Touch target, body size thực tế, text scaling và reflow 360/412dp vẫn chưa được xác minh. Theo làm rõ của người dùng, completion, nhánh thay thế và recovery vẫn được trình bày; không dùng một lần demo để đánh dấu mọi nhánh đạt.

## Liên kết persona — bổ sung 2026-10-15

Giữ nguyên 10 quyết định trên; không tuyên bố chúng đã được nghiên cứu lại với ba persona. [Ma trận truy vết](../ux/scenarios-and-tests.md#ma-trận-persona--need--ui-decision--test) dùng D01–D10 làm alias của số thứ tự hiện có: P01 ưu tiên quyết định 2–4, P02 ưu tiên 6–8, P03 ưu tiên 5 và 8. Đây là đối chiếu hiện tại để chuẩn bị review/test, không viết lại lý do lịch sử.

Hai Secondary mới và mọi giả định đều được ghi trong [ux/persona.md](../ux/persona.md); [T01–T08](../ux/scenarios-and-tests.md#kế-hoạch-test) mới là kế hoạch, chưa có kết quả pass.

