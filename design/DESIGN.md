# Expense Tracker - Design Specification

## 1. Design direction

Giao diện cần tạo cảm giác bình tĩnh, rõ ràng và đáng tin cậy. Ứng dụng không đánh giá người dùng vì đã chi nhiều; thay vào đó, nó giải thích số liệu và đưa ra hành động nhỏ có thể thực hiện.

### Design principles

1. Một màn hình có một hành động chính rõ ràng.
2. Số tiền và ngân sách quan trọng hơn trang trí.
3. Cảnh báo luôn có nguyên nhân và bước tiếp theo.
4. Form ngắn, giữ dữ liệu khi có lỗi.
5. Mọi trạng thái đều có phản hồi bằng text, icon và màu.

## 2. Color tokens

Các giá trị là baseline để dựng Figma; phải kiểm tra contrast trước khi xác nhận.

| Semantic token | Light value | Mục đích |
| --- | --- | --- |
| `color.primary` | `#146C5A` | CTA chính, selected navigation |
| `color.onPrimary` | `#FFFFFF` | Nội dung trên primary |
| `color.primaryContainer` | `#D5F5EC` | Highlight nhẹ |
| `color.onPrimaryContainer` | `#073C31` | Nội dung trên primary container |
| `color.background` | `#F7F9F8` | Nền ứng dụng |
| `color.surface` | `#FFFFFF` | Card, sheet, dialog |
| `color.surfaceVariant` | `#EDF2F0` | Input và khu vực phụ |
| `color.textPrimary` | `#17211E` | Nội dung chính |
| `color.textSecondary` | `#52605C` | Nội dung phụ |
| `color.outline` | `#73817D` | Border và divider |
| `color.success` | `#197A49` | Hoàn thành, ngân sách an toàn |
| `color.warning` | `#9A5B00` | Gần ngưỡng |
| `color.warningContainer` | `#FFE2B8` | Nền cảnh báo |
| `color.error` | `#BA1A1A` | Validation và lỗi destructive |
| `color.errorContainer` | `#FFDAD6` | Nền thông báo lỗi |

Không dùng `success`, `warning` hoặc `error` như tín hiệu duy nhất. Luôn kèm icon và nhãn.

## 3. Typography tokens

Font đề xuất: `Inter` hoặc font sans-serif tương đương có hỗ trợ tiếng Việt.

| Token | Size / line height | Weight | Dùng cho |
| --- | --- | --- | --- |
| `type.displaySmall` | 32 / 40 sp | 700 | Tổng tiền quan trọng |
| `type.headlineMedium` | 28 / 36 sp | 700 | Tiêu đề dashboard |
| `type.titleLarge` | 22 / 28 sp | 600 | Tiêu đề màn hình |
| `type.titleMedium` | 16 / 24 sp | 600 | Card title |
| `type.bodyLarge` | 16 / 24 sp | 400 | Nội dung chính |
| `type.bodyMedium` | 14 / 20 sp | 400 | Nội dung phụ |
| `type.labelLarge` | 14 / 20 sp | 600 | Button và chip |
| `type.labelMedium` | 12 / 16 sp | 600 | Caption ngắn |

Số tiền dùng tabular figures nếu font hỗ trợ.

## 4. Spacing and layout

| Token | Value |
| --- | --- |
| `space.1` | 4 dp |
| `space.2` | 8 dp |
| `space.3` | 12 dp |
| `space.4` | 16 dp |
| `space.5` | 20 dp |
| `space.6` | 24 dp |
| `space.8` | 32 dp |
| `space.10` | 40 dp |

- Frame chính: `360 x 800 dp`.
- Content padding: 16 dp.
- Khoảng giữa section: 24 dp.
- Khoảng giữa các item trong list: 8 dp.
- Nội dung dài cuộn theo chiều dọc.
- Bottom Navigation cố định; CTA không che item cuối.

## 5. Radius and elevation

| Token | Value | Dùng cho |
| --- | --- | --- |
| `radius.small` | 8 dp | Chip, small control |
| `radius.medium` | 12 dp | Input, button |
| `radius.large` | 16 dp | Card, dialog |
| `radius.full` | 999 dp | FAB, pill |
| `elevation.none` | 0 | Default surface |
| `elevation.low` | 1 | Card |
| `elevation.medium` | 3 | Bottom sheet, dialog |

## 6. Component rules

### Button

- Chiều cao tối thiểu 48 dp.
- Một primary button trong mỗi vùng hành động.
- Loading giữ nguyên chiều rộng và thay nội dung bằng progress indicator có label accessibility.

### Text field

- Label luôn hiển thị, không dùng placeholder thay label.
- Supporting/error text nằm ngay dưới field.
- Amount field dùng bàn phím số và hiển thị đơn vị VND.

### Financial card

- Có title, amount, supporting text và optional action.
- Trạng thái budget gồm icon, text label và progress.

### Transaction row

- Icon danh mục, merchant/note, ngày và amount.
- Amount căn phải; expense dùng dấu trừ nhưng không phụ thuộc màu đỏ.

### Dialog

- Title mô tả hành động.
- Body giải thích tác động.
- Destructive action dùng label cụ thể như `Xóa giao dịch`.

## 7. Navigation

Bottom Navigation gồm Home, Giao dịch, Ngân sách và Hồ sơ. Mỗi destination có icon và text label. Selected state dùng primary color và indicator; không chỉ đổi màu icon.

Add Expense là FAB hoặc primary action trên Home và Transactions. Không tạo tab riêng cho form.

## 8. State patterns

- Loading: skeleton theo cấu trúc thật; form submit dùng button loading.
- Empty: phân biệt chưa có dữ liệu và không có kết quả lọc.
- Error: nêu nguyên nhân dễ hiểu, giữ context và có Retry.
- Offline: cho biết dữ liệu đang xem có thể cũ và action nào chưa đồng bộ.
- Success: snackbar xác nhận và optional action như Undo hoặc View.

## 9. Content tone

Nên dùng:

- “Bạn đã dùng 78% ngân sách Ăn uống.”
- “Với tốc độ hiện tại, ngân sách có thể hết sớm 4 ngày.”
- “Không thể lưu vì kết nối bị gián đoạn. Dữ liệu của bạn vẫn được giữ.”

Không dùng:

- “Bạn tiêu quá nhiều.”
- “Thói quen tài chính của bạn không tốt.”
- “Có lỗi xảy ra.”

## 10. Responsive behavior

- 360-412 dp: giữ một cột; card giãn theo chiều ngang.
- Text scale lớn: amount và action wrap; không cắt nội dung tài chính quan trọng.
- Từ 600 dp: content có max-width 600 dp và căn giữa; form không kéo giãn toàn màn hình.
- Charts giữ text summary bên dưới khi không đủ chiều rộng.

