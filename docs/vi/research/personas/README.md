# Người dùng của Expense Tracker

> [English version](../../../en/research/personas/README.md). Đây là bản persona chính của dự án; bản tiếng Anh là bản dịch và được cập nhật sau bản tiếng Việt.

## Nhóm người dùng

Expense Tracker hướng đến sinh viên từ 18 đến 24 tuổi đang sống xa gia đình và tự quản lý tiền sinh hoạt. Họ chủ yếu dùng điện thoại Android, thường có nhiều khoản chi nhỏ trong ngày và không muốn sử dụng một công cụ tài chính phức tạp.

Thu nhập của nhóm này có thể là tiền gia đình gửi theo tháng, tiền làm thêm hoặc cả hai. Điều họ cần biết là mình đã chi bao nhiêu, còn bao nhiêu và một khoản chi mới sẽ ảnh hưởng thế nào đến phần còn lại của tháng.

## Vấn đề cần giải quyết

Sinh viên sống xa nhà cần một cách nhanh và dễ hiểu để ghi lại chi tiêu hằng ngày và theo dõi hạn mức theo danh mục. Khi ghi chép không đều, họ thường chỉ nhận ra mình đã tiêu quá nhiều lúc tháng gần kết thúc.

## Ba proto-persona

### Nguyễn Minh

Minh thường ghi khoản chi ngay sau khi thanh toán. Minh cần một form ngắn, phản hồi rõ và giữ được dữ liệu nếu mạng gặp lỗi.

Chi tiết: [P01, người ghi chi ngay lúc phát sinh](P.01.md).

### Trần Thảo

Thảo kiểm tra ngân sách trước những khoản chi đáng cân nhắc. Thảo quan tâm đến số tiền còn lại, lý do xuất hiện cảnh báo và các giao dịch đã tạo ra số liệu đó.

Chi tiết: [P02, người kiểm tra trước khi chi](P.02.md).

### Lê Huy

Huy rà soát giao dịch theo tuần hoặc vào cuối tháng. Huy cần tìm và sửa dữ liệu nhanh, xóa có xác nhận và khôi phục được khi thao tác nhầm.

Chi tiết: [P03, người rà soát và sửa sai](P.03.md).

Ba hồ sơ trên là proto-persona. Nhóm xây dựng chúng từ phạm vi sản phẩm và các giả định về hành vi, chưa từ phỏng vấn hoặc quan sát người dùng.

## Tiêu chí thành công

- Người dùng thêm một khoản chi và thấy ngân sách cập nhật trong dưới 20 giây.
- Từ Home, người dùng xác định danh mục có nguy cơ vượt ngân sách trong dưới 10 giây.
- Người dùng có thể sửa hoặc xóa nhầm giao dịch mà vẫn kiểm soát được dữ liệu. Thao tác xóa có bước xác nhận và hỗ trợ Undo.
- Người dùng chọn được tháng, tạo báo cáo PDF và mở báo cáo khi xử lý thành công.

Các tiêu chí này sẽ được dùng để viết scenario, user flow và kế hoạch kiểm thử cho những bước tiếp theo.
