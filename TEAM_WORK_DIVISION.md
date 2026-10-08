# Kế hoạch phân chia công việc nhóm (Team Work Division)

## PRM323 — Lab 2: Thiết kế UI/UX có hỗ trợ AI (Expense Tracker)

Tài liệu này xác định rõ trách nhiệm, phạm vi công việc và sản phẩm bàn giao cụ thể cho từng thành viên trong nhóm 3 người, nhằm tối ưu hóa tiến độ làm việc song song và đảm bảo đạt tối đa 100 điểm theo rubric của Lab 2.

---

## 1. Tổng quan phân chia trách nhiệm

```text
               ┌── Thành viên 1: Design System, Thư viện Component & Quy trình AI (Lead)
Nhóm 3 người ──┼── Thành viên 2: UI Màn hình Nhánh 1 (Flow 1 & Flow 2: Giao dịch & Nhập liệu)
               └── Thành viên 3: UI Màn hình Nhánh 2 (Flow 3: Ngân sách, Báo cáo) & Prototype
```

---

## 2. Chi tiết phân công từng thành viên

### 👤 Thành viên 1: Design System, Thư viện Component & Quy trình AI (Lead)

- **Trọng tâm:** Thiết lập nền tảng Design System trên Figma, chuẩn bị kho Component dùng chung và thực hiện trọn vẹn quy trình tạo/phản biện UI bằng AI (chiếm 30 điểm quy trình).

#### Phạm vi công việc:

1. **Thực thi quy trình AI & Ghi nhận bằng chứng:**
   - Sử dụng Google Stitch tạo UI ban đầu cho Flow 1 dựa trên ngữ cảnh từ `design/DESIGN.md`. Chụp ảnh lưu vào `assets/stitch/`.
   - Thực hiện 3 vòng lặp có ý nghĩa (Visual Hierarchy, Error Recovery, Contrast) và dùng AI phản biện theo 10 Usability Heuristics của Nielsen.
   - Hoàn thiện đầy đủ nội dung tài liệu `ai/ai-design-log.md` (prompt nguyên văn, ảnh trước/sau, bảng quyết định `accept`/`modify`/`reject` kèm lý do).
2. **Figma Page `04 Design System`:**
   - Thiết lập toàn bộ Figma Variables / Styles: Color tokens, Typography scale, Spacing (4, 8, 12, 16, 24, 32dp), Corner Radius, Elevation theo `design/DESIGN.md`.
3. **Figma Page `05 Components`:**
   - Dựng trọn bộ **9 Component bắt buộc** bằng Auto Layout và Variants có đầy đủ các trạng thái:
     - `Button`: Default, pressed, disabled, loading.
     - `Text field` / `Amount field`: Default, focused, filled, error, disabled.
     - `Card`: Default, pressed (Financial Card, Category Card).
     - `Navigation Bar`: 4 destinations kèm trạng thái được chọn (Selected state).
     - `App Bar`: Default, có action buttons.
     - `Dialog`: Confirmation Dialog và một biến thể Hủy/Lỗi.
     - `Loading state`: Skeleton / Spinner ở cấp màn hình.
     - `Empty state`: Icon minh họa, thông báo, nút hành động.
     - `Error state`: Thông báo, nguyên nhân dễ hiểu, nút thử lại (Retry).
4. **Figma Page `01 User Flow` & Page `02 Wireframe`:**
   - Đưa sơ đồ luồng từ `ux/user-flow.md` vào Page 01 và dựng bố cục Wireframe Low-fi tương ứng vào Page 02.
5. **Tổng kết tài liệu:**
   - Kiểm tra Checklist Accessibility trong `design/design-decisions.md` và export ảnh PNG các màn hình cuối vào `assets/figma/`.

---

### 👤 Thành viên 2: UI Màn hình Nhánh 1 (Flow 1 & Flow 2: Giao dịch & Nhập liệu)

- **Trọng tâm:** Dựng các màn hình cốt lõi liên quan đến Dashboard, Quản lý giao dịch và Thao tác nhập liệu trên Figma Page `03 Final UI` (kích thước chuẩn 360 × 800 dp).

#### Danh sách 6 màn hình phụ trách (Dựa trên `design/screen-spec.md`):

1. **`AU-01` — Login:** Màn hình đăng nhập Google Sign-in chuẩn kích thước, logo ứng dụng.
2. **`HM-01` — Home Dashboard:** Thẻ tổng số dư, hạn mức ngân sách tháng, top 5 giao dịch gần nhất, nút hành động nổi bật Thêm khoản chi.
3. **`TX-01` — Transaction List:** Danh sách giao dịch phân nhóm theo ngày, thanh tìm kiếm, bộ lọc danh mục và sắp xếp.
4. **`TX-02` — Add/Edit Expense:** Form nhập khoản chi (số tiền, danh mục, ngày, merchant, ghi chú).
5. **`TX-03` — Transaction Detail:** Màn hình chi tiết giao dịch kèm nút Chỉnh sửa và Xóa.
6. **`NT-01` — Notification Center:** Danh sách thông báo nhắc nhở và cảnh báo ngân sách.

#### Các biến thể trạng thái (State variants) đặt cạnh màn hình tương ứng:

- `HM-01`: Trạng thái rỗng (Empty State) khi tài khoản chưa có giao dịch.
- `TX-02`: Trạng thái lỗi xác thực (Validation Error State) khi nhập số tiền = 0 hoặc để trống trường bắt buộc.
- `TX-01`: Trạng thái Snackbar hoàn tác (Undo State) xuất hiện sau khi xác nhận xóa giao dịch.

#### Quy chuẩn bắt buộc khi thực hiện:

- **Tuyệt đối không detach component:** Sử dụng 100% component instances và design tokens do Thành viên 1 cung cấp trên Page 05.
- Đảm bảo độ tương phản text $\ge 4.5:1$ và touch target của các nút bấm $\ge 48 \times 48\text{ dp}$.
- Bố cục dùng Auto Layout và constraints co giãn tốt ở bề rộng 360 dp và 412 dp.

---

### 👤 Thành viên 3: UI Màn hình Nhánh 2 (Flow 3) & Prototype Tương tác

- **Trọng tâm:** Dựng các màn hình Quản lý ngân sách, Phân tích chi tiêu, Xuất báo cáo, Hồ sơ trên Figma Page `03 Final UI` và chịu trách nhiệm chính đấu nối tương tác cho toàn bộ Figma Page `06 Prototype`.

#### Danh sách 6 màn hình phụ trách (Dựa trên `design/screen-spec.md`):

1. **`BD-01` — Budget Dashboard:** Danh sách tiến độ ngân sách các danh mục (Ăn uống, Nhà trọ, Đi lại...) với thanh progress bar trực quan.
2. **`BD-02` — Budget Detail:** Xem chi tiết nguyên nhân biến động ngân sách và các giao dịch đóng góp vào danh mục đó.
3. **`BD-03` — Create/Edit Budget:** Form thiết lập hoặc điều chỉnh hạn mức ngân sách tháng.
4. **`IN-01` — Insights:** Biểu đồ cơ cấu phân bổ chi tiêu theo danh mục kèm phần văn bản tóm tắt tương đương.
5. **`EX-01` — Export Report:** Chọn khoảng thời gian báo cáo và màn hình xuất file PDF kết quả.
6. **`ST-01` — Profile:** Thông tin cá nhân sinh viên, cài đặt chung và nút Đăng xuất.

#### Các biến thể trạng thái (State variants) đặt cạnh màn hình tương ứng:

- `BD-01`: Trạng thái cảnh báo vàng (sắp vượt ngưỡng 80%) và trạng thái vượt trần đỏ (>100%).
- `IN-01`: Trạng thái rỗng (Empty State) khi chưa đủ số liệu để dựng biểu đồ insights.

#### Phụ trách chính Figma Page `06 Prototype`:

- Thiết lập **3 Flow Starting Points** rõ ràng:
  - **Flow 1 Starting Point:** Bắt đầu từ `HM-01` $\rightarrow$ Mở `TX-02` $\rightarrow$ Nhập chi tiêu $\rightarrow$ Trở về `HM-01` thấy ngân sách cập nhật tức thì.
  - **Flow 2 Starting Point:** Bắt đầu từ `TX-01` $\rightarrow$ Mở `TX-03` $\rightarrow$ Bấm Xóa $\rightarrow$ Mở Confirmation Dialog dạng **Overlay** $\rightarrow$ Xác nhận $\rightarrow$ Quay lại `TX-01` hiển thị Snackbar có nút **Undo** để phục hồi.
  - **Flow 3 Starting Point:** Bắt đầu từ `BD-01` $\rightarrow$ Xem `BD-02` $\rightarrow$ Điều hướng sang `EX-01` $\rightarrow$ Chuyển cảnh từ loading sang kết quả xuất file PDF thành công.
- Đảm bảo **100% không có ngõ cụt**, nút Back quay về đúng màn hình nguồn, điều hướng chính xác theo `ux/user-flow.md`.

---

## 3. Quy tắc phối hợp và kiểm tra chất lượng (Quality Gate)

1. **Nguyên tắc dùng chung Component:**
   - Thành viên 2 và 3 chỉ dùng instance từ Page `05 Components`. Nếu phát sinh nhu cầu component mới hoặc biến thể mới, yêu cầu Thành viên 1 bổ sung vào Page 05 thay vì tự vẽ rời rạc.
2. **Kiểm tra chéo (Cross-check):**
   - Trước khi nộp, cả 3 thành viên mở `handoff/flutter-handoff.md` đối chiếu lại toàn bộ 12 màn hình để đảm bảo các trường nhập liệu, nút bấm, thông báo lỗi và luồng điều hướng khớp hoàn toàn với đặc tả.
3. **Kiểm tra quyền truy cập:**
   - Link Figma phải được bật quyền: _"Anyone with the link can view"_ và kiểm tra lại bằng trình duyệt ẩn danh (Incognito window).
