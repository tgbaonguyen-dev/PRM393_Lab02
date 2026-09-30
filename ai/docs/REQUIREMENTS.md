# PRM323 - Lab 2: Thiết kế UI/UX có hỗ trợ AI

> Google Stitch -> Figma  
> Ngày: 28/09/2026  
> Tác giả: @Lam Phuong

Trong bài lab này, bạn thiết kế UI/UX cho ứng dụng di động bằng các công cụ AI, và bạn được chấm điểm dựa trên các quyết định thiết kế nhiều không kém các màn hình cuối cùng. Phần quy trình (phân tích, viết prompt, phản biện, lập luận) chiếm **45 điểm**; phần sản phẩm (UI, design system, prototype, handoff) chiếm **55 điểm**.

## Mục lục

- [1. Thông tin Lab](#1-thông-tin-lab)
- [2. Chuẩn đầu ra](#2-chuẩn-đầu-ra)
- [3. Nhiệm vụ](#3-nhiệm-vụ)
- [4. Quy trình bắt buộc](#4-quy-trình-bắt-buộc)
- [5. Yêu cầu sử dụng AI](#5-yêu-cầu-sử-dụng-ai)
- [6. Yêu cầu phân tích UX](#6-yêu-cầu-phân-tích-ux)
- [7. Yêu cầu Figma](#7-yêu-cầu-figma)
- [8. Repository và Flutter handoff](#8-repository-và-flutter-handoff)
- [9. Rubric chấm điểm (100 điểm)](#9-rubric-chấm-điểm-100-điểm)

## 1. Thông tin Lab

| Mục | Chi tiết |
| --- | --- |
| Môn học | PRM323 - Cross-Platform Application Development |
| Lab | Lab 2 - Thiết kế UI/UX có hỗ trợ AI |
| Hình thức làm bài | Cá nhân (trừ khi giảng viên thông báo làm nhóm) |
| Thời lượng / hạn nộp | [giảng viên điền] |
| Trọng số trong điểm môn học | [giảng viên điền] |
| Công cụ bắt buộc | Google Stitch, Figma (gói Education miễn phí), GitHub, một trợ lý AI tùy chọn để phản biện thiết kế |
| Nộp bài | Một link GitHub repository và một link Figma (ai có link đều xem được) |
| Viết code | Không. Không viết code Flutter trong lab này |

**Công cụ:** [Google Stitch](https://stitch.withgoogle.com/) · [Figma cho sinh viên và giáo viên](https://www.figma.com/education/)

## 2. Chuẩn đầu ra

Sau lab này, bạn có thể:

1. Xác định người dùng mục tiêu, vấn đề và kiến trúc thông tin (information architecture) trước khi mở bất kỳ công cụ thiết kế nào.
2. Viết prompt đủ ngữ cảnh để Google Stitch tạo ra UI dùng được, và tinh chỉnh qua nhiều vòng lặp.
3. Phản biện kết quả do AI tạo ra theo các heuristic về usability, tiêu chí accessibility và người dùng của bạn, rồi chấp nhận, chỉnh sửa hoặc từ chối từng đề xuất kèm lý do.
4. Xây dựng design system dựa trên token và các component tái sử dụng có đầy đủ trạng thái (state) trong Figma.
5. Viết đặc tả để một lập trình viên khác có thể cài đặt bằng Flutter mà không phải hỏi lại bạn.

## 3. Nhiệm vụ

Thiết kế một ứng dụng di động giải quyết vấn đề thực tế cho một nhóm người dùng cụ thể. UI cuối cùng phải có:

- Ít nhất **8 màn hình khác nhau** (dialog và các biến thể trạng thái không tính là màn hình riêng).
- Ít nhất **3 user flow hoàn chỉnh**, mỗi flow có điểm bắt đầu, mục tiêu và điểm kết thúc rõ ràng.
- Ít nhất **1 flow có nhánh lỗi hoặc phục hồi** (ví dụ: nhập sai, mất mạng hoặc hoàn tác).

### Chủ đề

Chọn trong danh sách dưới đây hoặc tự đề xuất, và được giảng viên duyệt trước ngày `[ngày]`. Hãy làm chủ đề cụ thể: viết “ứng dụng lập kế hoạch học cho sinh viên năm nhất có 6 môn và chưa có thói quen học cố định”, không viết “ứng dụng lập kế hoạch học”. Chủ đề trùng cả chủ đề lẫn persona với sinh viên khác sẽ không được duyệt.

- Student Course Planner (thời khóa biểu và chọn môn)
- Study Planner (buổi học hằng ngày và deadline)
- Campus Event App
- Expense Tracker
- Food Ordering App
- Habit Tracker
- Library App
- Internship Finder

## 4. Quy trình bắt buộc

Làm theo đúng thứ tự: **Analyze (phân tích) -> Generate (tạo) -> Critique (phản biện) -> Refine (tinh chỉnh) -> Prototype -> Handoff**. Mỗi giai đoạn tạo ra một sản phẩm mà giai đoạn sau phụ thuộc vào.

| # | Giai đoạn | Sản phẩm |
| ---: | --- | --- |
| 1 | Vấn đề và persona | `ux/persona.md` |
| 2 | Phân tích UX, information architecture, user flow | `ux/user-flow.md` |
| 3 | Bản mô tả thiết kế (màu, chữ, khoảng cách, tone, quy tắc component) | `design/DESIGN.md` |
| 4 | UI ban đầu trong Google Stitch | Prompt và ảnh chụp trong `ai/ai-design-log.md` |
| 5 | Ít nhất 3 vòng lặp với AI kèm phản biện bằng AI | Các mục log kèm quyết định |
| 6 | Wireframe và UI cuối cùng trong Figma | Figma page 02 và 03 |
| 7 | Design system và component | Figma page 04 và 05 |
| 8 | Prototype tương tác | Figma page 06 |
| 9 | Flutter handoff | `handoff/flutter-handoff.md` |

> **Lưu ý về công cụ:** Tính năng, hạn mức và cách export của Google Stitch thay đổi theo thời gian. Nếu không dùng được Stitch, hãy báo giảng viên trước khi bắt đầu; có thể được duyệt một công cụ AI tạo UI tương đương, nhưng yêu cầu về log vẫn giữ nguyên. Màn hình xuất từ công cụ AI thường đến dưới dạng các layer rời rạc, vì vậy hãy dựng lại trong Figma bằng Auto Layout, token và component thay vì dựa vào bản import.

### Tài liệu tham khảo

- [Google Stitch](https://stitch.withgoogle.com/)
- [Figma cho sinh viên và giáo viên](https://www.figma.com/education/)
- [Figma: Guide to auto layout](https://help.figma.com/hc/en-us/articles/360040451373-Guide-to-auto-layout)

## 5. Yêu cầu sử dụng AI

Bạn phải dùng AI và phải ghi lại cách dùng. **AI tạo ra; bạn quyết định.**

1. **UI ban đầu.** Tạo phiên bản UI đầu tiên bằng Google Stitch. Ghi lại nguyên văn toàn bộ prompt, từng chữ, và lưu ảnh chụp kết quả.
2. **Ba vòng lặp có ý nghĩa.** Một vòng lặp chỉ được tính khi nó nhắm vào một vấn đề cụ thể, có tên rõ (ví dụ: hành động chính không rõ, điều hướng quá sâu, contrast thấp, thiếu empty state) và khác với các vòng lặp còn lại. Lưu ảnh trước và sau. Yêu cầu AI “làm đẹp hơn” không được tính.
3. **Phản biện bằng AI.** Nhờ một trợ lý AI đánh giá UI của bạn theo 10 heuristic usability của Nielsen, các quy tắc accessibility cơ bản và persona của bạn. Giữ lại prompt và toàn bộ câu trả lời. Bản phản biện phải có ít nhất 5 phát hiện gắn với các màn hình cụ thể.
4. **Ghi nhận quyết định.** Với mỗi đề xuất quan trọng, ghi rõ bạn chấp nhận, chỉnh sửa hay từ chối, và vì sao. Lý do phải liên quan đến persona, một heuristic hoặc một ràng buộc thực tế (phạm vi, thời gian, nền tảng). “Mình thích” và “AI nói vậy” không phải lý do.
5. **Khai báo.** Ghi lại mọi công cụ AI bạn đã dùng, kể cả công cụ ngoài Stitch, và dùng cho mục đích gì.

### Tài liệu tham khảo

- [Nielsen Norman Group: 10 Usability Heuristics for User Interface Design](https://www.nngroup.com/articles/ten-usability-heuristics/)
- [W3C: Understanding WCAG 2.1 Success Criterion 1.4.3, Contrast (Minimum)](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
- [Google Stitch](https://stitch.withgoogle.com/)

## 6. Yêu cầu phân tích UX

### `ux/persona.md` phải có

- Một persona chính: tên, độ tuổi, vai trò, bối cảnh hằng ngày, mục tiêu, nỗi đau (pain point), thói quen dùng thiết bị và nhu cầu accessibility nếu có.
- Một câu phát biểu vấn đề.
- Một tiêu chí thành công đo được (ví dụ: “sinh viên thêm được một deadline mới trong dưới 20 giây”).

### `ux/user-flow.md` phải có

- Information architecture: danh sách màn hình và cấu trúc điều hướng (màn nào là cấp cao nhất, màn nào là màn lồng bên trong).
- Ít nhất 3 user flow, mỗi flow vẽ thành sơ đồ (dùng Mermaid cũng được) với điểm bắt đầu, mục tiêu, điểm kết thúc, nhánh thành công (happy path) và ít nhất một nhánh thay thế. Một flow phải có nhánh lỗi hoặc phục hồi.
- Một bảng ánh xạ mỗi flow sang các màn hình nó sử dụng.

### Tài liệu tham khảo

- [Nielsen Norman Group: Personas Make Users Memorable for Product Team Members](https://www.nngroup.com/articles/persona/)
- [Mermaid: Flowchart syntax](https://mermaid.js.org/syntax/flowchart.html)

## 7. Yêu cầu Figma

File Figma phải có đúng sáu page sau, theo đúng thứ tự:

| Page | Nội dung |
| --- | --- |
| `01 User Flow` | Các sơ đồ flow, mỗi flow liên kết tới các màn hình nó sử dụng |
| `02 Wireframe` | Bố cục low-fidelity của tất cả màn hình |
| `03 Final UI` | Tất cả màn hình cuối cùng, kích thước 360 × 800 dp, các biến thể trạng thái đặt cạnh màn hình tương ứng |
| `04 Design System` | Token: màu, typography, khoảng cách, bo góc, elevation |
| `05 Components` | Thư viện component tái sử dụng có variant |
| `06 Prototype` | Các flow có thể bấm được, mỗi flow có điểm bắt đầu được đặt rõ |

### Design system

Định nghĩa token bằng Figma Variables hoặc styles. Component phải dùng token; giá trị màu hoặc kích thước gán cứng bên trong component bị trừ điểm. Bắt buộc có light theme; dark theme không bắt buộc.

### Component tối thiểu

Mỗi component dựng bằng Auto Layout và variant:

| Component | Trạng thái bắt buộc |
| --- | --- |
| Button | Default, pressed, disabled, loading |
| Text field | Default, focused, filled, error, disabled |
| Card | Default, pressed (nếu bấm được) |
| Navigation (bottom bar hoặc tương đương) | Mỗi điểm đến ở trạng thái được chọn |
| App bar | Default, có action |
| Dialog | Xác nhận, và một biến thể hủy hoặc báo lỗi |
| Loading state | Ít nhất một pattern ở mức màn hình (skeleton hoặc spinner) |
| Empty state | Hình minh họa hoặc icon, thông báo, một hành động |
| Error state | Thông báo, nguyên nhân bằng ngôn ngữ dễ hiểu, hành động thử lại |

### Checklist accessibility và responsive

Ghi kết quả từng mục vào `design/design-decisions.md`.

- Độ tương phản (contrast) chữ tối thiểu **4.5:1** với văn bản thường và **3:1** với chữ lớn và các điều khiển UI (WCAG 2.x).
- Vùng chạm (touch target) tối thiểu **48 × 48 dp**.
- Chữ nội dung tối thiểu **14 sp**; không truyền đạt thông tin chỉ bằng màu sắc.
- Bố cục dùng constraint và Auto Layout, và đã kiểm tra ở chiều rộng **360 dp** và **412 dp**.
- Trong `handoff/flutter-handoff.md`, mô tả những gì thay đổi trên màn hình rộng hơn (từ **600 dp** trở lên). Bạn không cần thiết kế chúng.

### Prototype

Mỗi flow trong 3 flow của bạn phải bấm được từ đầu đến cuối mà không bị ngõ cụt. Thêm ít nhất một dialog mở dưới dạng overlay và một chuyển cảnh từ loading sang kết quả. Đặt flow starting point cho mỗi flow trong Figma.

### Tài liệu tham khảo

- [Figma: Guide to variables](https://help.figma.com/hc/en-us/articles/15339657135383-Guide-to-variables-in-Figma)
- [Figma: The difference between variables and styles](https://help.figma.com/hc/en-us/articles/15871097384471)
- [Figma: Guide to auto layout](https://help.figma.com/hc/en-us/articles/360040451373-Guide-to-auto-layout)
- [Figma: Create and use variants](https://help.figma.com/hc/en-us/articles/360056440594-Create-and-use-variants)
- [Figma: Create and manage component properties](https://help.figma.com/hc/en-us/articles/8883756012823-Create-and-manage-component-properties)
- [Figma: Guide to prototyping](https://help.figma.com/hc/en-us/articles/360040314193-Guide-to-prototyping-in-Figma)
- [Figma: Create and manage prototype flows](https://help.figma.com/hc/en-us/articles/360039823894-Create-and-manage-prototype-flows)
- [W3C: Understanding WCAG 2.1 Success Criterion 1.4.3, Contrast (Minimum)](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
- [Material Design 3: Accessibility designing](https://m3.material.io/foundations/designing/structure)
- [Flutter: Accessibility, UI design and styling](https://docs.flutter.dev/ui/accessibility/ui-design-and-styling)

## 8. Repository và Flutter handoff

Nộp một GitHub repository đặt tên `prm323-lab2-<student-id>` với cấu trúc sau:

```text
prm323-lab2-<student-id>/
├── README.md
├── ux/
│   ├── persona.md
│   └── user-flow.md
├── design/
│   ├── DESIGN.md
│   ├── screen-spec.md
│   └── design-decisions.md//
├── ai/
│   └── ai-design-log.md
├── assets/
│   ├── stitch/                 # Ảnh chụp mọi phiên bản do Stitch tạo
│   └── figma/                  # PNG export các màn hình cuối cùng
└── handoff/
    └── flutter-handoff.md
```
| File | Mục đích |
| --- | --- |
| `README.md` | Chủ đề, persona một dòng, link Figma, danh sách công cụ AI đã dùng và bản đồ nơi tìm từng sản phẩm |
| `design/DESIGN.md` | Bản mô tả thiết kế bạn đưa cho Stitch: màu, typography, khoảng cách, tone, quy tắc component |
| `design/screen-spec.md` | Mỗi màn hình dùng để làm gì, hiển thị nội dung gì, thuộc flow nào (ý đồ thiết kế) |
| `design/design-decisions.md` | Không quá 10 quyết định quan trọng nhất kèm lý do, cộng kết quả checklist accessibility |
| `ai/ai-design-log.md` | Mọi prompt, kết quả, phản biện và quyết định (template ở Phụ lục A) |
| `handoff/flutter-handoff.md` | Cách lập trình viên dựng ứng dụng (xem dưới) |

### Flutter handoff

Với mỗi màn hình, đặc tả đủ sáu mục:

1. **Layout:** cấu trúc từ trên xuống dưới (ví dụ `Scaffold -> AppBar -> Column` cuộn được), giá trị khoảng cách lấy từ token và phần nào cuộn.
2. **Components:** các component nào từ thư viện xuất hiện, kèm tên variant.
3. **States:** default, loading, empty, error và populated, tùy cái nào áp dụng.
4. **User interactions:** mỗi thao tác chạm, vuốt, nhập liệu và quy tắc validation, và kết quả của nó.
5. **Navigation:** người dùng đến từ đâu, mỗi hành động dẫn tới đâu và nút Back làm gì.
6. **Important UI constraints:** vùng chạm tối thiểu, hành vi bàn phím, quy tắc khi chữ tràn, độ dài nội dung tối đa, hành vi trên màn hình rộng hơn.

Cần có thêm hai bảng chung:

- **Token sang Flutter:** mỗi màu, text style và giá trị khoảng cách kèm tên dự kiến trong `ColorScheme`, `TextTheme` hoặc hằng số.
- **Component sang widget:** ví dụ Button sang `FilledButton`, Text field sang `TextFormField`, Navigation sang `NavigationBar`, Dialog sang `AlertDialog`.

Template ở Phụ lục B.

> **Kiểm tra handoff:** Một bạn cùng lớp phải dựng được một màn hình từ file handoff của bạn, chỉ mở Figma để xem giao diện. Bất cứ điều gì họ phải hỏi lại bạn đều là khoảng trống trong đặc tả.

### Tài liệu tham khảo

- [Flutter: Use themes to share colors and font styles](https://docs.flutter.dev/cookbook/design/themes)
- [Flutter API: ThemeData](https://api.flutter.dev/flutter/material/ThemeData-class.html)
- [Flutter: Material components (widget catalog)](https://docs.flutter.dev/ui/widgets/material)
- [Flutter: Navigation and routing](https://docs.flutter.dev/ui/navigation)
- [Flutter: Build a form with validation](https://docs.flutter.dev/cookbook/forms/validation)
- [Flutter: Adaptive and responsive design](https://docs.flutter.dev/ui/adaptive-responsive)

## 9. Rubric chấm điểm (100 điểm)

Mỗi tiêu chí con được chấm một trong ba mức: điểm tối đa, điểm một phần hoặc 0. Điểm một phần được cho khi yêu cầu đạt ở một mức nhất định, ví dụ đúng ở một số flow hoặc màn hình nhưng chưa đủ tất cả.

Các tiêu chí quy trình tổng cộng **45 điểm** (UX 15, tạo UI bằng AI 10, vòng lặp và phản biện 15, tài liệu 5); các tiêu chí sản phẩm tổng cộng **55 điểm**.

### 9.1. Phân tích UX và user flow - 15 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Người dùng mục tiêu và vấn đề | 5 | Persona cụ thể, có bối cảnh, mục tiêu, pain point; vấn đề một câu; tiêu chí thành công đo được | Persona chung chung (“sinh viên”); không có pain point; không có tiêu chí thành công |
| Information architecture | 5 | Có danh sách màn hình và cấu trúc điều hướng; mọi màn hình đều được ít nhất một flow sử dụng | Màn hình không thuộc flow nào; màn hình không thể truy cập; không có cấu trúc điều hướng |
| User flow | 5 | Ít nhất 3 flow có điểm bắt đầu, mục tiêu, điểm kết thúc, nhánh thay thế và bảng ánh xạ flow sang màn hình | Chỉ có happy path; dưới 3 flow; flow không ánh xạ sang màn hình |

### 9.2. Tạo UI bằng AI - 10 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Viết prompt | 5 | Prompt nêu rõ người dùng, nhiệm vụ, nền tảng, ràng buộc, phong cách (dựa trên `DESIGN.md`) và được ghi nguyên văn | Prompt một dòng; prompt không được ghi hoặc chỉ tóm tắt |
| UI ban đầu từ Stitch | 5 | UI được tạo bao phủ ít nhất flow chính, có ảnh chụp làm bằng chứng | Không có bằng chứng về kết quả của Stitch; kết quả chỉ có một màn hình |

### 9.3. Vòng lặp AI và phản biện UX - 15 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Ít nhất 3 vòng lặp có ý nghĩa | 5 | Mỗi vòng nhắm vào một vấn đề có tên khác nhau, có ảnh trước và sau | Dưới 3; chỉ đổi giao diện bề ngoài; các vòng lặp lặp lại cùng một thay đổi |
| Phản biện UX bằng AI | 5 | Bản phản biện dùng heuristic có tên, accessibility và persona; ít nhất 5 phát hiện gắn với màn hình | Phản biện chung chung; dưới 5 phát hiện; phát hiện không gắn với màn hình |
| Lập luận và quyết định của sinh viên | 5 | Mọi đề xuất quan trọng được đánh dấu chấp nhận, chỉnh sửa hoặc từ chối kèm lý do, và Figma phản ánh các quyết định đó | Không có lý do; chấp nhận hết mà không giải thích; quyết định không thấy trong UI cuối cùng |

### 9.4. Thiết kế UI/UX cuối cùng - 20 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Thứ bậc thị giác (visual hierarchy) | 5 | Mỗi màn hình có một hành động chính rõ ràng; thang cỡ chữ nhất quán; nhóm nội dung rõ | Nhiều hành động chính cạnh tranh nhau; cỡ chữ không nhất quán |
| Tính nhất quán | 5 | Cùng component, token, nhãn và pattern trên mọi màn hình | Cùng một thành phần nhìn khác hoặc đặt tên khác ở các màn hình khác nhau |
| Tính dễ dùng (usability) | 5 | Hoàn thành flow với ít bước; có phản hồi cho mọi hành động; phòng ngừa và phục hồi lỗi; có empty, loading, error state ở màn hình liên quan | Ngõ cụt; không phản hồi; thiếu state |
| Accessibility và responsive | 5 | Hoàn thành checklist ở mục 7 kèm bằng chứng; đã kiểm tra bố cục ở 360 dp và 412 dp | Contrast hoặc touch target không đạt; ý nghĩa chỉ bằng màu; thiếu checklist |

### 9.5. Design system và component - 15 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Design token | 5 | Màu, typography, khoảng cách, bo góc, elevation được định nghĩa thành Variables hoặc styles và được component sử dụng | Giá trị gán cứng; token định nghĩa nhưng không được dùng |
| Component tái sử dụng | 5 | Đủ 9 component tối thiểu dựng bằng Auto Layout và variant; màn hình dùng instance | Thiếu component; màn hình dùng bản sao đã detach |
| Trạng thái component | 5 | Mọi state bắt buộc ở mục 7 đều có và được sử dụng | Thiếu state hoặc chỉ vẽ thành các frame rời |

### 9.6. Prototype tương tác - 10 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Ít nhất 3 flow hoàn chỉnh | 5 | Mỗi flow bấm được từ đầu đến cuối, có starting point | Dưới 3 flow; flow đứt giữa chừng |
| Tương tác và điều hướng đúng | 5 | Back đúng; ít nhất một overlay và một chuyển cảnh loading sang kết quả; không ngõ cụt | Đích đến sai; không có Back; ngõ cụt |

### 9.7. Đặc tả Flutter handoff - 10 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Đặc tả màn hình | 5 | Mỗi màn hình có đủ 6 mục ở mục 8 | Thiếu màn hình; thiếu mục; chỉ mô tả giao diện |
| Component, state, tương tác, bảng ánh xạ | 5 | Bảng token sang Flutter và component sang widget đầy đủ; state và tương tác không mơ hồ | Lập trình viên phải hỏi lại mới dựng được màn hình |

### 9.8. Tài liệu và log sử dụng AI - 5 điểm

| Tiêu chí | Điểm | Điểm tối đa khi | Mất điểm khi |
| --- | ---: | --- | --- |
| Prompt và vòng lặp đầy đủ | 3 | Đủ prompt, kết quả, phản biện, quyết định và truy vết được tới ảnh chụp | Prompt bị tóm tắt hoặc thiếu; vòng lặp không có bằng chứng |
| Tài liệu rõ ràng | 2 | Repository đúng cấu trúc; README ánh xạ các sản phẩm; mọi link hoạt động | Sai cấu trúc; link hỏng hoặc đặt riêng tư |

> **Quy tắc truy cập:** Nếu link Figma không mở được tại thời điểm hết hạn, các tiêu chí dựa trên Figma (UI cuối cùng, design system, prototype) bị chấm 0 cho đến khi được sửa, và áp dụng chính sách nộp trễ.
