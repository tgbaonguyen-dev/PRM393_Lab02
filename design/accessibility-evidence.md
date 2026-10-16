# Bằng chứng tính contrast token

Kiểm tra lại ngày 2026-10-16, độc lập với folder thuyết trình. Nguồn: [DESIGN.md](DESIGN.md); phương pháp: relative luminance sRGB, contrast `(Lmax + 0.05) / (Lmin + 0.05)`. Chỉ áp dụng màu khai báo dạng opaque, không đọc Figma.

Các tỷ lệ dưới đây được tính theo công thức WCAG relative luminance sRGB từ token trong `DESIGN.md`. Script kiểm tra nội bộ không thuộc gói nộp; các giá trị và kết luận cần thiết được lưu trực tiếp tại đây.

| Foreground / background | Contrast làm tròn | Chữ thường ≥4.5:1 |
| --- | ---: | --- |
| onPrimary / primary | 6.32:1 | Đạt |
| textPrimary / surface | 16.50:1 | Đạt |
| textSecondary / surface | 6.59:1 | Đạt |
| warning / warningContainer | 4.35:1 | Chưa đạt |
| error / errorContainer | 5.00:1 | Đạt |
| onPrimaryContainer / primaryContainer | 10.65:1 | Đạt |

Kết luận: **5/6 cặp đạt**; phân loại dựa trên số chưa làm tròn. Warning cần sửa tại thiết kế nguồn rồi kiểm tra lại. Chưa chỉnh Figma/token trong lần sắp xếp repository này.

Đây không phải chứng nhận accessibility toàn màn hình: binding, nền thực tế, transparency, vùng chạm, cỡ chữ, text scaling và responsive 360/412dp vẫn cần kiểm riêng. Xem [checklist](design-decisions.md#accessibility-checklist).
