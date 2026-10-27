# P03: Lê Huy, người rà soát và sửa sai

> English version: [P03: Lê Huy](../../../en/research/personas/P.03.md).
>
> Trạng thái: Proto-persona. Hồ sơ này dựa trên phạm vi sản phẩm và các giả định về hành vi. Nhóm chưa kiểm chứng hồ sơ bằng nghiên cứu người dùng.

[Quay lại tổng quan persona](README.md).

**Vai trò:** Secondary persona  
**Tuổi:** 22  
**Bối cảnh:** Sinh viên năm cuối, sống xa gia đình, có thu nhập bán thời gian và thường rà soát chi tiêu theo tuần hoặc cuối tháng  
**Thiết bị chính:** Điện thoại Android  
**Mức độ am hiểu tài chính:** Trung bình

## Câu chuyện

Huy không ghi được mọi khoản chi ngay sau khi thanh toán. Cuối tuần hoặc cuối tháng, Huy mở lại Expense Tracker rồi đối chiếu với lịch sử ví điện tử và tài khoản ngân hàng. Huy cần các giao dịch chính xác để có thể tin vào tổng chi và ngân sách.

Một giao dịch có thể sai số tiền, nhầm danh mục hoặc bị nhập hai lần. Huy muốn sửa nhanh nhưng vẫn giữ được bộ lọc và vị trí đang xem. Trước khi xóa, Huy cần biết rõ giao dịch nào sẽ biến mất. Nếu vừa xác nhận nhầm, Huy cần Undo tiếp tục khả dụng cho đến khi chọn khôi phục hoặc chủ động đóng thông báo, kể cả sau khi mở lại ứng dụng. Báo cáo tháng chỉ hữu ích sau khi các con số đã khớp.

## Hành vi

- Rà soát giao dịch theo đợt, thường vào cuối tuần hoặc cuối tháng.
- Tìm giao dịch theo merchant, ngày hoặc danh mục.
- Lọc và sắp xếp danh sách để đối chiếu với nguồn khác.
- Sửa amount, category, date hoặc ghi chú khi phát hiện sai.
- Kiểm tra tổng chi và ngân sách sau mỗi lần sửa hoặc xóa.
- Chỉ xem báo cáo tháng sau khi tin rằng dữ liệu đã đủ.
- Dùng Undo ngay khi nhận ra mình vừa xóa nhầm.

## Mục tiêu

- Tìm đúng giao dịch trong một danh sách dài.
- Sửa dữ liệu mà không tạo giao dịch mới hoặc làm đổi trường khác.
- Biết rõ tác động trước khi xác nhận xóa.
- Khôi phục nhanh khi xóa nhầm.
- Giữ số liệu trên Home, Budgets và Insights nhất quán.
- Mở báo cáo tháng có thể đối chiếu với danh sách giao dịch.

## Nhu cầu

- Search, category filter và sort theo ngày hoặc số tiền.
- Transaction Detail hiển thị amount, category, date, merchant và note.
- Form edit giữ dữ liệu hiện tại và chỉ cập nhật trường đã sửa.
- Dialog xóa nêu rõ giao dịch và tác động.
- Snackbar Undo dễ thấy và dễ bấm.
- PDF có summary, category breakdown và transaction list.
- Back quay về đúng nguồn và giữ lại bộ lọc.

## Khó khăn

- Danh sách dài nhưng thiếu tìm kiếm hoặc bộ lọc hữu ích.
- Giao dịch thiếu thông tin để phân biệt các khoản giống nhau.
- Tổng chi không cập nhật đúng sau khi sửa.
- Thao tác xóa diễn ra ngay, không có confirmation.
- Không thể khôi phục giao dịch vừa xóa nhầm.
- Nút Back làm mất bộ lọc hoặc quay về sai màn hình.
- Báo cáo không ghi rõ kỳ dữ liệu và nội dung bên trong.

## Động lực

- Tin rằng số liệu trong ứng dụng khớp với chi tiêu thực tế.
- Phát hiện khoản ghi trùng hoặc phân loại sai.
- Có bản tổng hợp tháng rõ ràng để xem lại hoặc lưu trữ.

## Ràng buộc

- Có thể phải đối chiếu nhiều nguồn dữ liệu.
- Một số giao dịch có nội dung gần giống nhau.
- Việc rà soát thường dồn vào cuối tuần hoặc cuối tháng.
- Các hành động chỉnh sửa, hủy và xóa phải dễ phân biệt.
- Một thao tác sai không được làm hỏng phần dữ liệu đã kiểm tra.

## JTBD

> Khi tổng chi không khớp với kỳ vọng, tôi muốn tìm và sửa đúng giao dịch để có thể tin vào ngân sách và báo cáo cuối tháng.

## Tình huống chính

Cuối tháng, Huy mở Transaction List và lọc theo danh mục Ăn uống. Một giao dịch xuất hiện hai lần. Huy mở Transaction Detail rồi chọn xóa. Dialog xác nhận ghi rõ khoản sắp bị xóa. Sau khi Huy xác nhận, danh sách và ngân sách được tính lại, đồng thời Snackbar hiện nút Undo. Huy kiểm tra lại rồi chủ động đóng Snackbar để hoàn tất việc xóa. Khi các số liệu đã khớp, Huy xem Insights và mở báo cáo PDF.

## Tiêu chí thành công

- Tìm được giao dịch cần sửa bằng search, filter hoặc sort.
- Edit chỉ thay đổi dữ liệu đã chọn và cập nhật tổng chính xác.
- Cancel không xóa dữ liệu.
- Undo khôi phục đúng giao dịch một lần và tính lại ngân sách.
- Báo cáo hiển thị đúng tháng, summary, category breakdown và transaction list.
- Back quay về đúng nguồn mà không làm mất ngữ cảnh.

## Hàm ý thiết kế

- Transaction List cần search, category filter và sort rõ ràng.
- Transaction Row phải có đủ thông tin để phân biệt các khoản tương tự.
- Edit Expense dùng lại form và điền sẵn dữ liệu hiện tại.
- Delete luôn mở confirmation dialog, sau đó cung cấp Undo nếu xóa thành công.
- Thay đổi giao dịch phải cập nhật Dashboard, Budget và Insights đồng bộ.
- Export Report có đủ các trạng thái default, processing, ready và failed.
