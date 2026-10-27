# P01: Nguyễn Minh, người ghi chi ngay lúc phát sinh

> English version: [P01: Nguyễn Minh](../../../en/research/personas/P.01.md).
>
> Trạng thái: Proto-persona. Hồ sơ này dựa trên phạm vi sản phẩm và các giả định về hành vi. Nhóm chưa kiểm chứng hồ sơ bằng nghiên cứu người dùng.

[Quay lại tổng quan persona](README.md).

**Vai trò:** Primary persona  
**Tuổi:** 21  
**Bối cảnh:** Sinh viên năm ba, sống xa gia đình và tự quản lý tiền sinh hoạt hằng tháng  
**Thiết bị chính:** Điện thoại Android  
**Mức độ am hiểu tài chính:** Cơ bản

## Câu chuyện

Minh nhận tiền sinh hoạt vào đầu tháng và kiếm thêm một khoản nhỏ từ công việc bán thời gian. Các khoản chi thường không lớn: tiền ăn, đi lại, đồ dùng học tập và vài dịch vụ số. Minh từng ghi chi tiêu trong ứng dụng ghi chú, nhưng bỏ dở vì mỗi lần nhập mất nhiều thời gian mà không cho biết ngân sách đã thay đổi ra sao.

Khoản chi còn dễ nhớ ngay sau lúc thanh toán. Đến cuối ngày, Minh có thể quên hẳn hoặc chỉ nhớ một con số gần đúng. Vì thế, Minh cần ghi nhanh ngay cả khi đang đi bộ, đứng xếp hàng hoặc chỉ rảnh một tay.

## Hành vi

- Ghi khoản chi ngay sau khi thanh toán hoặc trong cùng ngày.
- Ưu tiên số tiền, danh mục và ngày. Cửa hàng và ghi chú chỉ được nhập khi cần thêm ngữ cảnh.
- Mở lại Home sau khi lưu để kiểm tra ngân sách.
- Dùng lịch sử ví điện tử hoặc ngân hàng để bổ sung những khoản đã quên.
- Dễ bỏ ghi nếu form dài, phản hồi chậm hoặc bắt nhập lại sau lỗi.
- Mỗi lần chỉ dùng ứng dụng trong một khoảng thời gian ngắn.

## Mục tiêu

- Ghi khoản chi trước khi quên.
- Hoàn thành thao tác nhanh mà không cần hướng dẫn.
- Biết giao dịch đang lưu, đã lưu hay gặp lỗi.
- Thấy ngay tổng chi và ngân sách còn lại sau khi lưu.
- Duy trì thói quen ghi chép mà không thấy nặng nề.

## Nhu cầu

- Form ngắn, các trường bắt buộc dễ nhận biết.
- Bàn phím số và định dạng VND dễ đọc.
- Dữ liệu đã nhập vẫn còn sau lỗi validation hoặc lỗi mạng.
- Retry không tạo giao dịch trùng.
- Thông báo thành công xác nhận cả giao dịch và ngân sách đã cập nhật.
- Nút Back không làm mất dữ liệu chưa lưu mà không báo trước.

## Khó khăn

- Form có quá nhiều trường.
- Không rõ trường nào bắt buộc hoặc lỗi nằm ở đâu.
- Nút lưu phản hồi chậm, khiến Minh dễ bấm nhiều lần.
- Dữ liệu vừa nhập biến mất khi kết nối bị gián đoạn.
- Không chắc giao dịch đã được ghi nhận.
- Tổng tiền sai do thiếu giao dịch hoặc lưu trùng.

## Động lực

- Biết tiền của mình đã được dùng vào đâu.
- Tránh bị bất ngờ khi gần cuối tháng.
- Quản lý tiền mà không phải học các khái niệm tài chính phức tạp.

## Ràng buộc

- Thời gian và mức độ tập trung thấp trong lúc nhập.
- Kết nối mạng đôi khi không ổn định.
- Thường thao tác bằng một tay trên màn hình nhỏ.
- Không quen thuật ngữ kế toán hoặc biểu đồ tài chính phức tạp.
- Nội dung cần dễ đọc, tương phản rõ và có vùng chạm đủ lớn.

## JTBD

> Khi vừa thanh toán một khoản chi, tôi muốn ghi lại nhanh trước khi quên để số tiền còn lại phản ánh đúng tình hình của mình.

## Tình huống chính

Sau khi trả tiền bữa trưa, Minh mở Expense Tracker từ Home và chọn "Thêm khoản chi". Minh nhập số tiền, chọn danh mục Ăn uống rồi giữ nguyên ngày mặc định. Nút lưu hiển thị trạng thái đang xử lý sau khi được nhấn. Nếu mất mạng, form vẫn giữ các giá trị để Minh thử lại. Khi lưu xong, giao dịch mới xuất hiện và ngân sách Ăn uống cũng thay đổi.

## Tiêu chí thành công

- Thêm một khoản chi và thấy ngân sách cập nhật trong dưới 20 giây.
- Không phải nhập lại dữ liệu sau lỗi validation hoặc lỗi mạng.
- Retry không tạo giao dịch trùng.
- Giao dịch mới chỉ xuất hiện một lần.
- Hiểu số tiền còn lại mà không cần tự tính.

## Hàm ý thiết kế

- "Thêm khoản chi" cần dễ thấy trên Home và Transactions.
- Form tập trung vào số tiền, danh mục và ngày. Merchant và ghi chú là tùy chọn.
- Lỗi xuất hiện ngay cạnh trường liên quan.
- Trạng thái submitting ngăn người dùng gửi lại trong lúc hệ thống đang xử lý.
- Khi mạng lỗi, form giải thích nguyên nhân, giữ input và cho phép Retry.
- Sau khi lưu, giao dịch và ngân sách phải cập nhật cùng nhau.
