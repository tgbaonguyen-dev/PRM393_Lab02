# Expense Tracker - Product Requirements

## 1. Product summary

Expense Tracker là ứng dụng mobile-first giúp sinh viên sống xa nhà ghi nhận chi tiêu nhanh, biết ngân sách còn lại và phát hiện sớm nguy cơ tiêu quá mức trước cuối tháng.

Sản phẩm tập trung vào vòng lặp:

> Ghi khoản chi -> ngân sách cập nhật -> hiểu xu hướng -> điều chỉnh hành vi -> xuất báo cáo.

## 2. Target user

Đối tượng chính là sinh viên 18-24 tuổi:

- Sống xa gia đình và tự quản lý tiền sinh hoạt.
- Nhận tiền theo tháng hoặc có thêm thu nhập bán thời gian.
- Chủ yếu sử dụng điện thoại Android.
- Có nhiều khoản chi nhỏ và thường quên ghi chép.
- Muốn biết mình còn có thể chi bao nhiêu thay vì xem báo cáo tài chính phức tạp.

## 3. Problem statement

Sinh viên sống xa nhà cần một cách nhanh và dễ hiểu để ghi nhận khoản chi hằng ngày và theo dõi hạn mức theo danh mục, vì việc ghi chép không đều khiến họ chỉ nhận ra đã tiêu quá nhiều khi tháng gần kết thúc.

## 4. Success criteria

- Người dùng thêm một khoản chi và thấy ngân sách cập nhật trong dưới 20 giây.
- Người dùng xác định được danh mục có nguy cơ vượt ngân sách trong dưới 10 giây từ Home.
- Người dùng sửa hoặc xóa nhầm giao dịch mà không mất kiểm soát dữ liệu.
- Người dùng xuất được báo cáo tháng bằng PDF qua một flow rõ ràng.

## 5. MVP scope

### In scope

- Google Sign-In được thể hiện trong thiết kế để chuẩn bị cho Lab 3.
- Dashboard tháng.
- Danh sách, tìm kiếm, lọc và sắp xếp giao dịch.
- Thêm, xem, sửa và xóa khoản chi.
- Danh mục chi tiêu.
- Tạo và chỉnh sửa ngân sách tháng theo danh mục.
- Cảnh báo sắp vượt hoặc đã vượt ngân sách.
- Insights cơ bản theo danh mục.
- Xuất báo cáo PDF.
- Profile, Notification Center và sign out.
- Loading, empty, validation error, network error và undo state.

### Out of scope

- OCR hóa đơn và camera processing.
- Đồng bộ ngân hàng hoặc ví điện tử.
- Chuyển tiền và thanh toán.
- Mạng xã hội và chi phí nhóm.
- AI financial coach.
- Quản lý đầu tư, nợ, bảo hành hoặc tài sản.
- Multi-currency và tỷ giá.
- iOS, web admin và subscription billing.

## 6. Functional requirements

### FR-01 Authentication

- Người chưa đăng nhập chỉ thấy Login.
- Người dùng đăng nhập bằng Google.
- Profile hiển thị avatar, tên và email.
- Người dùng có thể đăng xuất.

### FR-02 Dashboard

- Hiển thị tổng chi tháng, ngân sách còn lại và phần trăm đã sử dụng.
- Hiển thị tối đa năm giao dịch gần nhất.
- Hiển thị tối đa ba danh mục chi nhiều nhất.
- Có hành động chính `Thêm khoản chi`.
- Có trạng thái loading, empty, populated và error.

### FR-03 Transaction management

- Người dùng xem danh sách và chi tiết giao dịch.
- Người dùng thêm, sửa và xóa giao dịch.
- Trường bắt buộc: số tiền, danh mục và ngày.
- Trường tùy chọn: merchant và ghi chú.
- Số tiền phải lớn hơn 0.
- Xóa cần confirmation dialog và hỗ trợ Undo.
- Danh sách có lọc theo danh mục và sắp xếp theo ngày hoặc số tiền.

### FR-04 Budget management

- Người dùng tạo ngân sách tháng cho một danh mục.
- Hạn mức phải lớn hơn 0.
- Một danh mục chỉ có một ngân sách trong cùng kỳ.
- Tiến độ được tính từ các giao dịch thuộc đúng danh mục và kỳ.
- Trạng thái: an toàn, sắp đạt ngưỡng, vượt hạn mức.
- Trạng thái không được biểu đạt chỉ bằng màu.

### FR-05 Insights

- Hiển thị tổng chi và phân bổ theo danh mục trong tháng.
- Biểu đồ có legend và text summary tương đương.
- Người dùng có thể mở danh sách giao dịch nguồn của một danh mục.
- Có empty state khi chưa đủ dữ liệu.

### FR-06 PDF export

- Người dùng chọn tháng và tạo báo cáo PDF.
- Báo cáo gồm summary, breakdown theo danh mục và danh sách giao dịch.
- UI thể hiện processing, ready và failed states.
- Khi thành công, người dùng có thể mở báo cáo.

### FR-07 Notifications and profile

- Notification Center hiển thị cảnh báo ngân sách và trạng thái đã đọc.
- Chạm thông báo mở đúng Budget Detail.
- Profile chứa thông tin tài khoản và các action phục vụ demo Lab 3.

## 7. Information architecture

Điều hướng chính có bốn destination:

- Home
- Transactions
- Budgets
- Profile

`Add Expense` là hành động nổi bật từ Home và Transactions. Insights mở từ Home. Export Report mở từ Insights hoặc Profile. Notification Center mở từ App Bar hoặc Profile.

## 8. Data entities prepared for Lab 3

### UserProfile

- `id`
- `displayName`
- `email`
- `photoUrl`
- `currencyCode`

### Transaction

- `id`
- `ownerId`
- `amount`
- `categoryId`
- `merchant`
- `note`
- `occurredAt`
- `createdAt`
- `updatedAt`

### Category

- `id`
- `name`
- `iconName`
- `colorToken`

### Budget

- `id`
- `ownerId`
- `categoryId`
- `month`
- `limitAmount`
- `warningThreshold`

### ExportReport

- `id`
- `ownerId`
- `month`
- `fileName`
- `fileUrl`
- `itemCount`
- `createdAt`

### AppNotification

- `id`
- `ownerId`
- `type`
- `title`
- `body`
- `targetId`
- `isRead`
- `createdAt`

## 9. Content principles

- Ngôn ngữ ngắn, trung tính, không phán xét.
- Không dùng các câu như “Bạn tiêu quá tệ” hoặc “Bạn thất bại”.
- Cảnh báo giải thích nguyên nhân và đề xuất bước tiếp theo.
- Số tiền luôn có đơn vị và định dạng nhất quán.
- Action nguy hiểm mô tả rõ tác động trước khi xác nhận.

## 10. Acceptance criteria

- Có ít nhất 10 màn hình được sử dụng trong ba flow.
- Mọi action chính có phản hồi trực quan.
- Form giữ dữ liệu người dùng khi validation hoặc network error.
- Budget cập nhật nhất quán sau khi thêm, sửa hoặc xóa giao dịch.
- Không có ngõ cụt trong prototype.
- UI đạt checklist accessibility và responsive của Lab 2.

