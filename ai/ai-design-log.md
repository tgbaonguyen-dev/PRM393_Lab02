# AI Design Log

Tài liệu này phải được cập nhật trong lúc làm. Không điền kết quả, quyết định hoặc đường dẫn ảnh nếu chưa thực hiện thật.

## 1. AI tools declaration

| Công cụ | Mục đích | Ngày sử dụng | Bằng chứng |
| --- | --- | --- | --- |
| ChatGPT/Codex | Phân tích đề, thu gọn phạm vi và soạn tài liệu nền | 2026-10-06 | Repository documents |
| Google Stitch | Tạo UI ban đầu | Chưa thực hiện | `[BỔ SUNG]` |
| Công cụ khác | `[BỔ SUNG]` | `[BỔ SUNG]` | `[BỔ SUNG]` |

## 2. Initial Google Stitch generation

### Mục tiêu

Tạo UI ban đầu bao phủ Flow 1 - Thêm khoản chi và các màn hình liên quan.

### Prompt nguyên văn

```text
[DÁN NGUYÊN VĂN PROMPT ĐÃ GỬI CHO GOOGLE STITCH]
```

### Kết quả

- Ngày/giờ: `[BỔ SUNG]`
- Màn hình được tạo: `[BỔ SUNG]`
- Ảnh: `assets/stitch/initial-[tên-màn-hình].png`
- Nhận xét ban đầu: `[BỔ SUNG SAU KHI XEM KẾT QUẢ]`

## 3. Iteration 1 - Visual hierarchy

### Vấn đề cụ thể

`[Ví dụ cần xác minh: hành động Thêm khoản chi chưa nổi bật trên Home]`

### Prompt nguyên văn

```text
[DÁN PROMPT]
```

### Bằng chứng

- Before: `assets/stitch/iteration-1-before.png`
- After: `assets/stitch/iteration-1-after.png`

### Quyết định

- Trạng thái: `[Chấp nhận / Chỉnh sửa / Từ chối]`
- Lý do liên quan persona/heuristic/ràng buộc: `[BỔ SUNG]`
- Figma frame phản ánh quyết định: `[BỔ SUNG LINK/FRAME]`

## 4. Iteration 2 - Error recovery

### Vấn đề cụ thể

`[Ví dụ cần xác minh: form không giữ dữ liệu khi lưu thất bại]`

### Prompt nguyên văn

```text
[DÁN PROMPT]
```

### Bằng chứng

- Before: `assets/stitch/iteration-2-before.png`
- After: `assets/stitch/iteration-2-after.png`

### Quyết định

- Trạng thái: `[Chấp nhận / Chỉnh sửa / Từ chối]`
- Lý do: `[BỔ SUNG]`
- Figma frame: `[BỔ SUNG]`

## 5. Iteration 3 - Accessibility and budget status

### Vấn đề cụ thể

`[Ví dụ cần xác minh: trạng thái ngân sách chỉ phân biệt bằng màu]`

### Prompt nguyên văn

```text
[DÁN PROMPT]
```

### Bằng chứng

- Before: `assets/stitch/iteration-3-before.png`
- After: `assets/stitch/iteration-3-after.png`

### Quyết định

- Trạng thái: `[Chấp nhận / Chỉnh sửa / Từ chối]`
- Lý do: `[BỔ SUNG]`
- Figma frame: `[BỔ SUNG]`

## 6. AI critique

### Prompt nguyên văn

Prompt cần yêu cầu đánh giá theo 10 Nielsen heuristics, WCAG contrast/touch target và persona Nguyễn Minh; mỗi finding phải nêu màn hình, vấn đề, mức độ, heuristic và đề xuất.

```text
[DÁN NGUYÊN VĂN PROMPT PHẢN BIỆN]
```

### Toàn bộ câu trả lời

```text
[DÁN TOÀN BỘ CÂU TRẢ LỜI, KHÔNG TÓM TẮT]
```

## 7. Finding decisions

| # | Màn hình | Finding | Heuristic/accessibility | Quyết định | Lý do | Figma evidence |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | `[BỔ SUNG]` | `[BỔ SUNG]` | `[BỔ SUNG]` | `[BỔ SUNG]` | `[BỔ SUNG]` | `[BỔ SUNG]` |
| 2 |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  |

## 8. Final declaration

- [ ] Mọi prompt được lưu nguyên văn.
- [ ] Mọi ảnh before/after tồn tại và mở được.
- [ ] Có ít nhất 3 iteration khác nhau.
- [ ] Có ít nhất 5 findings gắn với màn hình.
- [ ] Mọi finding quan trọng có quyết định và lý do.
- [ ] Final UI phản ánh các quyết định đã chấp nhận/chỉnh sửa.

