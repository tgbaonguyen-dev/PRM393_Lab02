# Tiêu chí hoàn thành Lab 2

Lab 2 được xem là hoàn thành khi đáp ứng toàn bộ các tiêu chí dưới đây. Bài lab chỉ thiết kế UI/UX; không viết code Flutter.

## 1. Phạm vi và đề tài

- [ ] Ứng dụng giải quyết một vấn đề thực tế cho một nhóm người dùng cụ thể.
- [ ] Đề tài và persona không trùng cả chủ đề lẫn persona với sinh viên khác.
- [ ] Đề tài tự đề xuất đã được giảng viên duyệt trước hạn quy định.
- [ ] Minh chứng thể hiện bài được thực hiện đúng thứ tự bắt buộc: Analyze → Generate → Critique → Refine → Prototype → Handoff.
- [ ] UI có ít nhất 8 màn hình khác nhau; dialog và biến thể trạng thái không được tính là màn hình riêng.
- [ ] Có ít nhất 3 user flow hoàn chỉnh, mỗi flow có điểm bắt đầu, mục tiêu và điểm kết thúc rõ ràng.
- [ ] Mỗi flow có happy path và ít nhất một nhánh thay thế.
- [ ] Ít nhất một flow có nhánh lỗi hoặc phục hồi.

## 2. Phân tích UX

### `ux/persona.md`

- [ ] Có một persona chính gồm tên, tuổi, vai trò và bối cảnh hằng ngày.
- [ ] Mô tả mục tiêu, pain point, thói quen sử dụng thiết bị và nhu cầu accessibility nếu có.
- [ ] Có problem statement một câu.
- [ ] Có ít nhất một tiêu chí thành công đo được.

### `ux/user-flow.md`

- [ ] Có information architecture gồm danh sách màn hình và cấu trúc điều hướng.
- [ ] Phân biệt rõ màn hình cấp cao nhất và màn hình lồng bên trong.
- [ ] Có sơ đồ cho ít nhất 3 user flow.
- [ ] Mỗi sơ đồ thể hiện điểm bắt đầu, mục tiêu, điểm kết thúc, happy path và nhánh thay thế.
- [ ] Có ít nhất một nhánh lỗi hoặc phục hồi trong các flow.
- [ ] Có bảng ánh xạ từng flow sang các màn hình được sử dụng.
- [ ] Mọi màn hình đều thuộc ít nhất một flow và có thể truy cập được.

## 3. Bản mô tả và đặc tả thiết kế

### `design/DESIGN.md`

- [ ] Mô tả màu sắc, typography, spacing, corner radius và elevation.
- [ ] Mô tả tone hình ảnh, tone nội dung và quy tắc component.
- [ ] Nội dung đủ cụ thể để dùng làm ngữ cảnh cho prompt Google Stitch.

### `design/screen-spec.md`

- [ ] Mỗi màn hình có mục đích rõ ràng.
- [ ] Mỗi màn hình mô tả nội dung cần hiển thị.
- [ ] Mỗi màn hình được ánh xạ tới user flow liên quan.

### `design/design-decisions.md`

- [ ] Ghi không quá 10 quyết định thiết kế quan trọng nhất kèm lý do.
- [ ] Lý do dựa trên persona, usability heuristic, accessibility hoặc ràng buộc thực tế.
- [ ] Có kết quả checklist accessibility và responsive cho từng mục bắt buộc.

## 4. Sử dụng AI và bằng chứng

### UI ban đầu bằng Google Stitch

- [ ] Prompt nêu rõ người dùng, nhiệm vụ, nền tảng, danh sách màn hình, flow, ràng buộc và phong cách từ `design/DESIGN.md`.
- [ ] Prompt được lưu nguyên văn trong `ai/ai-design-log.md`, không tóm tắt.
- [ ] UI ban đầu bao phủ ít nhất một flow chính, không chỉ có một màn hình đơn lẻ.
- [ ] Ảnh chụp toàn bộ kết quả ban đầu được lưu trong `assets/stitch/` và có tên dễ truy vết.

### Ba vòng lặp có ý nghĩa

- [ ] Có ít nhất 3 vòng lặp, mỗi vòng xử lý một vấn đề cụ thể và khác nhau.
- [ ] Mỗi vòng có tên vấn đề, prompt nguyên văn, ảnh trước và sau, cùng kết quả quan sát được.
- [ ] Các vòng lặp cải thiện usability, accessibility hoặc nhu cầu của persona, không chỉ yêu cầu “làm đẹp hơn”.

### Phản biện và quyết định

- [ ] Có prompt yêu cầu AI đánh giá theo 10 Nielsen usability heuristics, accessibility cơ bản và persona.
- [ ] Lưu nguyên văn prompt và toàn bộ câu trả lời phản biện của AI.
- [ ] Bản phản biện có ít nhất 5 phát hiện gắn với màn hình cụ thể.
- [ ] Mọi đề xuất quan trọng được đánh dấu `accept`, `modify` hoặc `reject`.
- [ ] Mỗi quyết định có lý do dựa trên persona, heuristic, accessibility hoặc ràng buộc thực tế.
- [ ] UI cuối trong Figma phản ánh được các quyết định đã ghi.
- [ ] Khai báo tất cả công cụ AI đã sử dụng và mục đích sử dụng của từng công cụ.

## 5. File Figma

- [ ] File có đúng 6 page theo đúng thứ tự:
  1. `01 User Flow`
  2. `02 Wireframe`
  3. `03 Final UI`
  4. `04 Design System`
  5. `05 Components`
  6. `06 Prototype`
- [ ] `01 User Flow` chứa các sơ đồ flow và liên kết flow với màn hình tương ứng.
- [ ] `02 Wireframe` chứa wireframe low-fidelity của tất cả màn hình.
- [ ] `03 Final UI` chứa tất cả màn hình cuối ở kích thước 360 × 800 dp; biến thể trạng thái đặt cạnh màn hình liên quan.
- [ ] `04 Design System` chứa token màu, typography, spacing, corner radius và elevation.
- [ ] `05 Components` chứa thư viện component tái sử dụng và các variant bắt buộc.
- [ ] `06 Prototype` chứa các flow có thể tương tác và starting point rõ ràng.
- [ ] Light theme được thiết kế đầy đủ; dark theme không bắt buộc.

## 6. Chất lượng UI, design system và component

### UI cuối

- [ ] Mỗi màn hình có một hành động chính rõ ràng, visual hierarchy và nhóm nội dung hợp lý.
- [ ] Typography, nhãn, component, token và interaction pattern nhất quán giữa các màn hình.
- [ ] Flow được tối giản hợp lý và mọi thao tác đều có phản hồi.
- [ ] Các màn hình liên quan có populated, loading, empty và error state phù hợp.
- [ ] Error state giải thích nguyên nhân bằng ngôn ngữ dễ hiểu và có hành động phục hồi.

### Design system

- [ ] Token được định nghĩa bằng Figma Variables hoặc styles.
- [ ] Component sử dụng token; không gán cứng màu hoặc kích thước bên trong component.
- [ ] Component được dựng bằng Auto Layout và variant.
- [ ] Màn hình dùng component instance, không dùng bản sao đã detach.
- [ ] Có đủ component và trạng thái bắt buộc:

| Component | Trạng thái bắt buộc |
| --- | --- |
| Button | Default, pressed, disabled, loading |
| Text field | Default, focused, filled, error, disabled |
| Card | Default, pressed nếu có thể bấm |
| Navigation | Mỗi destination có selected state |
| App bar | Default, có action |
| Dialog | Confirm và một biến thể cancel hoặc error |
| Loading state | Skeleton hoặc spinner ở cấp màn hình |
| Empty state | Icon hoặc hình minh họa, thông báo và một hành động |
| Error state | Thông báo, nguyên nhân dễ hiểu và hành động Retry |

## 7. Accessibility và responsive

- [ ] Contrast của chữ thường đạt tối thiểu 4.5:1.
- [ ] Contrast của chữ lớn và UI control đạt tối thiểu 3:1.
- [ ] Touch target đạt tối thiểu 48 × 48 dp.
- [ ] Body text có kích thước tối thiểu 14 sp.
- [ ] Không truyền đạt thông tin chỉ bằng màu sắc.
- [ ] Layout sử dụng constraints và Auto Layout.
- [ ] Layout đã được kiểm tra ở chiều rộng 360 dp và 412 dp.
- [ ] `handoff/flutter-handoff.md` mô tả thay đổi của layout ở chiều rộng từ 600 dp trở lên.
- [ ] Kết quả kiểm tra được ghi trong `design/design-decisions.md`.

## 8. Prototype

- [ ] Cả 3 flow có starting point riêng và có thể bấm từ đầu đến cuối.
- [ ] Điều hướng tiến, quay lại và hủy đúng ngữ cảnh.
- [ ] Không có màn hình ngõ cụt hoặc liên kết sai đích.
- [ ] Có ít nhất một dialog mở dưới dạng overlay.
- [ ] Có ít nhất một chuyển cảnh từ loading sang kết quả.

## 9. Flutter handoff

### Đặc tả từng màn hình trong `handoff/flutter-handoff.md`

- [ ] `Layout`: cấu trúc từ trên xuống dưới, token spacing và vùng cuộn.
- [ ] `Components`: component sử dụng và tên variant.
- [ ] `States`: các state áp dụng như default, loading, empty, error và populated.
- [ ] `User interactions`: thao tác chạm, vuốt, nhập liệu, validation và kết quả.
- [ ] `Navigation`: nguồn truy cập, đích đến của từng hành động và hành vi Back.
- [ ] `Important UI constraints`: touch target, keyboard, text overflow, giới hạn nội dung và hành vi trên màn hình rộng.

### Ánh xạ triển khai

- [ ] Có bảng ánh xạ toàn bộ design token sang `ColorScheme`, `TextTheme` hoặc hằng số Flutter dự kiến.
- [ ] Có bảng ánh xạ Figma component sang Flutter widget.
- [ ] Đặc tả đủ rõ để một sinh viên khác dựng được một màn hình mà không phải hỏi thêm về hành vi hoặc thông số; Figma chỉ dùng để đối chiếu giao diện.

## 10. Repository và nộp bài

- [ ] Repository được đặt tên `prm323-lab2-<student-id>`.
- [ ] Repository có đủ cấu trúc:

```text
prm323-lab2-<student-id>/
├── README.md
├── ux/
│   ├── persona.md
│   └── user-flow.md
├── design/
│   ├── DESIGN.md
│   ├── screen-spec.md
│   └── design-decisions.md
├── ai/
│   └── ai-design-log.md
├── assets/
│   ├── stitch/
│   └── figma/
└── handoff/
    └── flutter-handoff.md
```

- [ ] `README.md` có chủ đề, persona một dòng, link Figma, danh sách công cụ AI và bản đồ đường dẫn tới từng deliverable.
- [ ] Final UI được export thành PNG vào `assets/figma/`.
- [ ] Prompt, ảnh chụp và quyết định trong log có thể truy vết lẫn nhau.
- [ ] Mọi đường dẫn trong repository hoạt động.
- [ ] Nộp một link GitHub repository và một link Figma.
- [ ] Link Figma cho phép bất kỳ ai có link xem được và đã được kiểm tra bằng cửa sổ ẩn danh.

