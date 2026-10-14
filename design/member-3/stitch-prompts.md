# Thành viên 3 — Prompt thiết kế Google Stitch

Phạm vi: BD-01, BD-02, BD-03, IN-01, EX-01, ST-01 và các state thuộc các màn hình này. Nội dung dưới đây được chuẩn bị trước khi gửi. Chưa phải bằng chứng đã chạy Stitch.

## Prompt 1 — Sáu màn hình chính

```text
Extend the existing Expense Tracker project with exactly six new Android mobile screens for team member 3. Preserve all existing screens and match the project's existing visual language. This is a student expense tracker, in Vietnamese, for Nguyễn Minh, a student living away from home. Design calm, clear Material 3 UI with restrained decoration, generous spacing, financial numbers as the visual priority, rounded white cards on #F7F9F8, primary green #146C5A and pale green #D5F5EC. Use Inter with Vietnamese support; normal body text >=14px; primary numbers 32px bold; screen headings 22px semibold. Use 16px horizontal padding, 8/12/16/24px spacing, 12px input/button radius and 16px card radius. Every interactive target must be at least 48x48px. Base frame 360x800px, flexible at 412px; long content scrolls vertically. Bottom navigation is fixed on root screens only, with exactly Home, Giao dịch, Ngân sách, Hồ sơ, including icon and text and a selected pill indicator. Nested screens have a visible Back button. Use real Vietnamese labels, not lorem ipsum. All money uses Vietnamese separators and đ. Do not create login, home, transaction entry/list/detail, notification screens, or a new design system; those belong to other team members.

Create these six named screens:

1. BD-01 — Ngân sách. Selected tab Ngân sách. Month selector “Tháng 10, 2026”; monthly summary “Đã chi 4.050.000 đ”, “Hạn mức 6.000.000 đ”, “Còn 1.950.000 đ”. Three budget category cards: Ăn uống 1.200.000/2.000.000 đ (60%, Trong ngân sách); Nhà trọ 2.400.000/3.000.000 đ (80%, Sắp vượt ngân sách); Đi lại 450.000/1.000.000 đ (45%, Trong ngân sách). Each card has a category icon/name, spent/limit, progress bar, actual percentage and status in text plus icon. Legend clarifies safe below 80%, warning 80–100%, exceeded above 100%. One primary CTA “Tạo ngân sách”; secondary action “Xem phân tích”. Cards open budget detail.

2. BD-02 — Ngân sách Ăn uống. Back button. Month “Tháng 10, 2026”. Large spent value 1.800.000 đ, limit 2.000.000 đ, remaining 200.000 đ, 90% amber progress and icon+text warning. Neutral explanation: “Bạn đã dùng 90% ngân sách Ăn uống. Còn 200.000 đ đến cuối tháng.” Primary CTA “Điều chỉnh hạn mức”. Three contributing transaction rows reconcile exactly to spent: Siêu thị thực phẩm 700.000 đ on 12/10/2026; Bữa ăn tuần 2 500.000 đ on 10/10/2026; Bữa ăn tuần 1 600.000 đ on 05/10/2026. Secondary actions “Xem giao dịch nguồn” and “Phân tích & báo cáo”. Keep content scrollable; no bottom navigation on this nested screen.

3. BD-03 — Tạo ngân sách. Back button. Short labeled form: Danh mục dropdown, Hạn mức tháng numeric amount with fixed VND unit, Cảnh báo khi đạt numeric percentage field default 80% and helper “Từ 50 đến 100%”, Tháng áp dụng selector “Tháng 10, 2026”. Hint: “Mỗi danh mục chỉ có một ngân sách trong tháng.” Sticky primary “Lưu ngân sách” and secondary “Hủy”. Show focus-friendly outlines; labels remain visible. Use numeric threshold entry rather than slider-only. Default new budget category should be “Học tập”, which does not duplicate an existing budget; limit example 500.000 đ. Add a second mode later for editing an existing budget.

4. IN-01 — Phân tích chi tiêu. Back button and period selector. Total 4.650.000 đ, data through 13/10/2026. Readable category distribution chart with legend: Nhà trọ 2.400.000 đ (51,6%); Ăn uống 1.800.000 đ (38,7%); Đi lại 450.000 đ (9,7%). Provide an equivalent visible text summary below the chart: “Nhà trọ là khoản chi lớn nhất: 2.400.000 đ, chiếm 51,6%. Ăn uống chiếm 38,7%, Đi lại chiếm 9,7%.” Category rows can open filtered source transactions. Include top expenses from the same sample dataset. Primary CTA “Xuất báo cáo”. Do not convey chart information with color alone.

5. EX-01 — Xuất báo cáo. Back button. Period selector “Tháng 10, 2026” with visible range “01–31/10/2026”. Report contents card with selectable inclusions: Tổng chi & cơ cấu theo danh mục; Ngân sách, hạn mức & cảnh báo; Danh sách giao dịch. PDF preview summary with period and three categories. Primary CTA “Tạo PDF”. Below it, export history row “Tháng 9, 2026 · Chi-tieu-09-2026.pdf” with open action. Do not invent download URLs or claim an actual file was generated. This screen is a UI mockup.

6. ST-01 — Hồ sơ. Selected tab Hồ sơ. Initial avatar “NM”; sample student name “Nguyễn Minh”, sample email “minh@example.com”, subtitle “Sinh viên”. Settings groups: Thông báo ngân sách; Xuất báo cáo PDF; Đơn vị tiền tệ VND; Ngôn ngữ Tiếng Việt. Separate “Demo Lab 3” section with Remote Config values: Ngưỡng cảnh báo mặc định 80%, Báo cáo PDF đang bật; a clearly labeled “Crashlytics · Chỉ dùng kiểm thử” entry. Destructive secondary “Đăng xuất” separated from normal settings. No real account data.

Ensure summary arithmetic reconciles, all dates are in October 2026, no clipped amounts, normal text contrast at least 4.5:1, touch targets at least 48px, no gradient-heavy styling, and no floating CTA covering the final row. Keep each screen editable and consistently named by its ID.
```

## Prompt 2 — Các biến thể bắt buộc và phản hồi xuất PDF

```text
Using the six member-3 screens just created, duplicate only the relevant screens into named state variants. Keep original default frames and all other project screens intact. Place the state variants beside their source screens and preserve all visual styling, sizes, spacing and components.

BD-01 / Warning: change Ăn uống to 1.800.000 / 2.000.000 đ, 90%, amber icon+label “Sắp vượt ngân sách”; monthly spent 4.650.000 đ, limit 6.000.000 đ, remaining 1.350.000 đ. Keep Nhà trọ 2.400.000 and Đi lại 450.000.

BD-01 / Exceeded: change Ăn uống to 2.200.000 / 2.000.000 đ, 110%, red icon+label “Vượt ngân sách”; clamp the drawn bar to full width, retain actual label 110%, and display “Vượt 200.000 đ”. Monthly spent 5.050.000 đ, limit 6.000.000 đ, remaining 950.000 đ. Explain that the category exceeded its own limit even though the total monthly budget still has remaining funds.

IN-01 / Empty: same header and period selector, remove chart and top transactions; calm empty illustration, title “Chưa có dữ liệu phân tích”, text “Tháng này chưa có khoản chi. Thêm một khoản chi để xem cơ cấu chi tiêu.” Primary action “Thêm khoản chi”; Back remains available. Disable export when there is no data.

EX-01 / Processing: preserve chosen period and content, show a labeled progress indicator “Đang tạo báo cáo PDF…” and button loading state that prevents duplicate export. Include text “Lựa chọn của bạn được giữ nguyên.”

EX-01 / Ready: success icon+text “Báo cáo đã sẵn sàng”, file card “Chi-tieu-10-2026.pdf”, period 01–31/10/2026, primary “Mở PDF”, secondary “Tạo báo cáo khác”; Back returns to the actual source. This represents a prototype state, not an actual generated download.

EX-01 / Failed: error icon+text “Không tải báo cáo lên được vì mất kết nối. Kiểm tra mạng rồi thử lại.” Retain period and checked contents; primary “Thử lại”, secondary Back.

BD-03 / Edit: title “Điều chỉnh ngân sách”, category Ăn uống, current limit 2.000.000 đ, new entered limit 2.500.000 đ, threshold 80%, month October 2026, primary “Lưu thay đổi”. After saving, budget detail shows spent 1.800.000 đ / new limit 2.500.000 đ = 72%, remaining 700.000 đ, safe icon+label.

BD-03 / Validation Error: keep entered values; invalid limit 0 with inline “Hạn mức phải lớn hơn 0 đ.” and invalid threshold 40 with inline “Ngưỡng cảnh báo phải từ 50 đến 100%.” Both errors include an icon, red outline, and readable text. Include an explicit duplicate-category/month error for a separate attempted create of Ăn uống in October: “Ăn uống đã có ngân sách tháng 10. Chọn danh mục khác hoặc điều chỉnh ngân sách hiện tại.” Do not use color alone.

ST-01 / Sign-out confirmation overlay: dimmed profile background with centered confirmation dialog, title “Đăng xuất khỏi tài khoản?”, body “Dữ liệu đã lưu vẫn được giữ. Bạn cần đăng nhập lại để tiếp tục quản lý chi tiêu.” Actions “Ở lại” and “Đăng xuất”. Cancel closes the overlay and returns to the same profile.

Do not create screens owned by team member 2. Provide the mobile screens themselves, not a written explanation.
```

## Prototype trong Figma sau khi có quyền sửa

- Flow 1 bắt đầu HM-01; dùng frame HM/TX của thành viên 2; lưu → loading → TX-03 → HM-01 cập nhật.
- Flow 2 bắt đầu TX-01; TX-03 → overlay xác nhận xóa → TX-01 có Undo → phục hồi.
- Flow 3 bắt đầu BD-01; BD-02 → chỉnh ngân sách hoặc Insights → EX-01 → Processing → Ready → mở bản xem PDF.
- Back dùng nguồn thực tế; Hủy đóng overlay; lỗi có đường thử lại. Không xem các màn hình Stitch là bằng chứng đã hoàn thành prototype Figma.
