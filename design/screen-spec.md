# Screen Specification

## AU-01 - Login

- **Mục đích:** Cho phép người dùng đăng nhập bằng Google.
- **Nội dung:** Logo/tên ứng dụng, value proposition ngắn, nút Google Sign-In, liên kết privacy.
- **Hành động chính:** Tiếp tục với Google.
- **States:** Default, loading, authentication error, offline.
- **Đi tới:** HM-01 sau khi đăng nhập thành công.
- **Flow:** Entry gate cho cả ba flow.

## HM-01 - Home Dashboard

- **Mục đích:** Trả lời “Tháng này mình đã chi bao nhiêu và cần làm gì tiếp theo?”.
- **Nội dung:** App bar, tổng chi, ngân sách còn lại, budget warning, top categories, recent transactions, FAB.
- **Hành động chính:** Thêm khoản chi.
- **States:** Loading skeleton, first-use empty, populated, partial error, offline cache.
- **Đi tới:** TX-02, TX-03, BD-02, IN-01, NT-01.
- **Flow:** Flow 1.

## TX-01 - Transaction List

- **Mục đích:** Tìm và quản lý giao dịch.
- **Nội dung:** Search, filter chips, sort action, grouped list, FAB.
- **Hành động chính:** Mở chi tiết hoặc thêm khoản chi.
- **States:** Loading, no transactions, no filter result, populated, error, offline.
- **Đi tới:** TX-02, TX-03.
- **Flow:** Flow 2 và Flow 3.

## TX-02 - Add/Edit Expense

- **Mục đích:** Tạo hoặc sửa khoản chi trong thời gian ngắn.
- **Nội dung:** Amount, category, date, merchant, note, sticky submit button.
- **Validation:** Amount bắt buộc và lớn hơn 0; category và date bắt buộc; note tối đa 200 ký tự.
- **Hành động chính:** Lưu khoản chi.
- **States:** Default, focused, validation error, submitting, network error.
- **Đi tới:** TX-03 khi thành công.
- **Flow:** Flow 1 và Flow 2.

## TX-03 - Transaction Detail

- **Mục đích:** Xem nguồn dữ liệu và các hành động quản lý.
- **Nội dung:** Amount, category, merchant, date, note, edit và delete actions.
- **Hành động chính:** Chỉnh sửa.
- **Hành động nguy hiểm:** Xóa qua confirmation dialog.
- **States:** Loading, populated, error, delete confirmation, deleting.
- **Đi tới:** TX-02 hoặc TX-01.
- **Flow:** Flow 1 và Flow 2.

## BD-01 - Budget Dashboard

- **Mục đích:** Xem nhanh ngân sách nào an toàn hoặc cần chú ý.
- **Nội dung:** Summary tháng, category budget cards, status legend, add budget action.
- **Hành động chính:** Tạo ngân sách.
- **States:** Loading, no budgets, populated, error, offline.
- **Đi tới:** BD-02, BD-03.
- **Flow:** Flow 3.

## BD-02 - Budget Detail

- **Mục đích:** Giải thích tiến độ và các giao dịch tạo ra kết quả.
- **Nội dung:** Limit, spent, remaining, progress, status explanation, contributing transactions.
- **Hành động chính:** Điều chỉnh ngân sách.
- **States:** Safe, warning, exceeded, loading, error.
- **Đi tới:** BD-03, TX-01 filtered, IN-01.
- **Flow:** Flow 3.

## BD-03 - Create/Edit Budget

- **Mục đích:** Thiết lập hạn mức tháng theo danh mục.
- **Nội dung:** Category selector, limit amount, warning threshold, month.
- **Validation:** Limit lớn hơn 0; threshold từ 50 đến 100%; không trùng category trong cùng tháng.
- **Hành động chính:** Lưu ngân sách.
- **States:** Default, focused, validation error, submitting, network error.
- **Đi tới:** BD-02.
- **Flow:** Flow 3.

## IN-01 - Insights

- **Mục đích:** Giải thích phân bổ chi tiêu trong tháng.
- **Nội dung:** Period selector, total, category chart, text summary, top transactions, export action.
- **Hành động chính:** Xuất báo cáo.
- **States:** Loading, insufficient data, populated, error.
- **Đi tới:** TX-01 filtered, EX-01.
- **Flow:** Flow 3.

## EX-01 - Export Report

- **Mục đích:** Tạo báo cáo PDF theo tháng.
- **Nội dung:** Month, report contents, file preview summary, export history.
- **Hành động chính:** Tạo PDF.
- **States:** Default, processing, ready, upload failed, expired.
- **Đi tới:** PDF viewer/open action; Back về IN-01 hoặc ST-01 theo nguồn.
- **Flow:** Flow 3.

## NT-01 - Notification Center

- **Mục đích:** Tập trung cảnh báo ngân sách và trạng thái hệ thống.
- **Nội dung:** Notification list, unread indicator, timestamp, mark all read.
- **Hành động chính:** Mở cảnh báo.
- **States:** Loading, empty, populated, error.
- **Đi tới:** BD-02 theo `targetId`.
- **Flow:** Nhánh thay thế của Flow 3.

## ST-01 - Profile

- **Mục đích:** Quản lý tài khoản và các entry phục vụ Lab 3.
- **Nội dung:** Avatar, name, email, notifications, export reports, Remote Config values, Crashlytics demo controls, sign out.
- **Hành động chính:** Mở cài đặt liên quan; sign out là destructive/secondary action.
- **States:** Default, offline, sign-out confirmation.
- **Đi tới:** NT-01, EX-01, AU-01.
- **Flow:** Nhánh thay thế của Flow 3.

