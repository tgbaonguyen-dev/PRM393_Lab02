# Yêu cầu PRM393 Lab 2

Tài liệu này là checklist làm bài được chuẩn hóa từ đề Lab 2. Khi có khác biệt, đề bài gốc và hướng dẫn trực tiếp của giảng viên được ưu tiên.

## 1. Phạm vi bắt buộc

- Thiết kế ứng dụng di động giải quyết một vấn đề thực tế cho một nhóm người dùng cụ thể.
- Có ít nhất 8 màn hình khác nhau. Dialog và biến thể state không tính là màn hình riêng.
- Có ít nhất 3 user flow hoàn chỉnh, mỗi flow có điểm bắt đầu, mục tiêu và điểm kết thúc rõ ràng.
- Mỗi flow có happy path và ít nhất một nhánh thay thế.
- Có ít nhất một nhánh lỗi hoặc phục hồi.
- Không viết Flutter trong Lab 2.

## 2. Quy trình bắt buộc

Thực hiện theo thứ tự:

1. Analyze: persona, problem statement, success criterion.
2. Analyze: information architecture và user flow.
3. Define: màu sắc, typography, spacing, tone và component rules.
4. Generate: tạo UI ban đầu bằng Google Stitch.
5. Critique: thực hiện ít nhất 3 vòng lặp có vấn đề cụ thể và khác nhau.
6. Refine: dựng wireframe và Final UI trong Figma.
7. Systemize: tạo token và component variants.
8. Prototype: kết nối 3 flow từ đầu đến cuối.
9. Handoff: viết đặc tả Flutter đủ để người khác triển khai.

## 3. Bằng chứng sử dụng AI

- Lưu nguyên văn prompt Google Stitch và ảnh kết quả ban đầu.
- Có ít nhất 3 vòng tinh chỉnh; mỗi vòng ghi vấn đề, prompt, ảnh trước/sau và quyết định.
- Yêu cầu AI phản biện theo Nielsen heuristics, accessibility và persona.
- Bản phản biện có ít nhất 5 phát hiện gắn với màn hình cụ thể.
- Với mỗi đề xuất quan trọng, ghi `Chấp nhận`, `Chỉnh sửa` hoặc `Từ chối` cùng lý do.
- Khai báo tất cả công cụ AI đã sử dụng và mục đích.

Không tạo lại log sau khi hoàn thành. Nhật ký phải được cập nhật trong quá trình làm và liên kết tới bằng chứng thật.

## 4. Cấu trúc Figma bắt buộc

File Figma có đúng sáu page theo thứ tự:

1. `01 User Flow`
2. `02 Wireframe`
3. `03 Final UI`
4. `04 Design System`
5. `05 Components`
6. `06 Prototype`

Final UI dùng frame `360 x 800 dp`. Đặt các biến thể state cạnh màn hình tương ứng.

## 5. Design system và component

Token được định nghĩa bằng Figma Variables hoặc Styles và phải được component sử dụng:

- Color
- Typography
- Spacing
- Radius
- Elevation

Component tối thiểu:

| Component | State bắt buộc |
| --- | --- |
| Button | Default, pressed, disabled, loading |
| Text field | Default, focused, filled, error, disabled |
| Card | Default, pressed nếu bấm được |
| Navigation | Mỗi destination có selected state |
| App bar | Default và có action |
| Dialog | Confirm và cancel/error |
| Loading | Pattern cấp màn hình |
| Empty | Icon/illustration, message, action |
| Error | Message, nguyên nhân dễ hiểu, retry action |

Mọi component dùng Auto Layout, variants và semantic tokens. Màn hình dùng component instance, không detach.

## 6. Accessibility và responsive

- Contrast: `4.5:1` cho chữ thường; `3:1` cho chữ lớn và UI controls.
- Touch target tối thiểu `48 x 48 dp`.
- Body text tối thiểu `14 sp`.
- Không truyền đạt thông tin chỉ bằng màu.
- Kiểm tra layout ở chiều rộng `360 dp` và `412 dp`.
- Handoff mô tả hành vi từ `600 dp` trở lên.
- Ghi kết quả thật vào `design/design-decisions.md`.

## 7. Prototype

- Ba flow đều bấm được từ đầu đến cuối và có starting point.
- Back quay về đúng nguồn, không tạo ngõ cụt.
- Có ít nhất một dialog dạng overlay.
- Có ít nhất một chuyển cảnh loading sang kết quả.

## 8. Flutter handoff

Mỗi màn hình có đủ:

1. Layout.
2. Components và variants.
3. States.
4. User interactions và validation.
5. Navigation và Back behavior.
6. Important UI constraints.

Ngoài ra phải có bảng token-to-Flutter và component-to-widget.

## 9. Checklist trước khi nộp

- [ ] Repository mở được bằng cửa sổ riêng tư.
- [ ] Figma mở được với quyền xem bằng link.
- [ ] README có topic, persona, Figma link, công cụ AI và deliverable map.
- [ ] Có ít nhất 8 màn hình Final UI.
- [ ] Có đủ 3 flow và bảng flow-to-screen.
- [ ] Có nhánh lỗi/phục hồi.
- [ ] Có đủ 6 page Figma đúng thứ tự.
- [ ] Component và state bắt buộc đã hoàn thành.
- [ ] Accessibility checklist có bằng chứng thật.
- [ ] Prototype không có ngõ cụt.
- [ ] Handoff có đủ sáu mục cho mọi màn hình.
- [ ] AI log có prompt nguyên văn và ảnh trước/sau.

