# P02: Trần Thảo, người kiểm tra trước khi chi

> English version: [P02: Trần Thảo](../../../en/research/personas/P.02.md).
>
> Trạng thái: Proto-persona. Hồ sơ này dựa trên phạm vi sản phẩm và các giả định về hành vi. Nhóm chưa kiểm chứng hồ sơ bằng nghiên cứu người dùng.

[Quay lại tổng quan persona](README.md).

**Vai trò:** Secondary persona  
**Tuổi:** 20  
**Bối cảnh:** Sinh viên năm hai, sống ở trọ và quản lý một khoản sinh hoạt phí cố định mỗi tháng  
**Thiết bị chính:** Điện thoại Android  
**Mức độ am hiểu tài chính:** Cơ bản đến trung bình

## Câu chuyện

Thảo chia tiền sinh hoạt thành các nhóm như ăn uống, nhà trọ, đi lại và học tập. Thảo không cần theo dõi theo kiểu kế toán. Điều Thảo muốn biết là danh mục nào đang tiêu nhanh hơn dự kiến và một khoản chi mới sẽ ảnh hưởng thế nào đến những ngày còn lại trong tháng.

Một số ứng dụng chỉ cho Thảo xem tổng chi hoặc biểu đồ phần trăm. Sau khi xem, Thảo vẫn phải tự tính xem mình còn bao nhiêu tiền. Cảnh báo chỉ có màu đỏ hoặc vàng cũng khó hiểu vì không nói rõ nguyên nhân. Thảo cần số tiền còn lại, trạng thái ngân sách và những giao dịch đã tạo ra con số đó.

## Hành vi

- Mở Home trước một khoản chi không thường xuyên hoặc có giá trị đáng cân nhắc.
- Chú ý đến số tiền còn lại nhiều hơn tổng chi đứng riêng lẻ.
- So sánh ngân sách còn lại với số ngày còn lại trong tháng.
- Mở Budget Detail khi một danh mục có cảnh báo.
- Kiểm tra giao dịch nguồn để hiểu nguyên nhân của số liệu.
- Chỉ sửa hạn mức khi kế hoạch hoặc hoàn cảnh thực sự thay đổi.
- Xem Insights vào giữa hoặc cuối tháng để nhận ra xu hướng.

## Mục tiêu

- Nhận ra nhanh danh mục cần chú ý.
- Biết còn có thể chi bao nhiêu trong từng danh mục.
- Hiểu vì sao ngân sách đang an toàn, sắp hết hoặc đã vượt.
- Điều chỉnh cách chi trước khi tiền hết.
- Có đủ thông tin để quyết định giữ hay sửa hạn mức.

## Nhu cầu

- Số tiền còn lại, phần trăm đã dùng và hạn mức được đặt cạnh nhau.
- Cảnh báo có icon, nhãn và số liệu; màu sắc chỉ đóng vai trò hỗ trợ.
- Budget Detail giải thích nguyên nhân và liệt kê các giao dịch liên quan.
- Insights có legend và phần tóm tắt bằng chữ tương đương biểu đồ.
- Nội dung cảnh báo trung tính, không trách móc.
- Khi hạn mức thay đổi, percentage và remaining được tính lại chính xác.

## Khó khăn

- Chỉ thấy tổng chi mà không biết còn có thể chi bao nhiêu.
- Phần trăm thiếu số tiền hoặc mốc thời gian để đối chiếu.
- Cảnh báo không nêu nguyên nhân hay bước tiếp theo.
- Trạng thái chỉ được phân biệt bằng màu.
- Biểu đồ không giúp đưa ra quyết định.
- Không mở được các giao dịch đứng sau một con số tổng hợp.
- Cách viết khiến người dùng thấy bị phán xét khi vượt ngân sách.

## Động lực

- Giữ tiền sinh hoạt đủ dùng đến cuối tháng.
- Tự tin hơn khi biết rõ giới hạn còn lại.
- Phát hiện rủi ro sớm, trước khi số tiền còn lại quá ít.

## Ràng buộc

- Ngân sách tháng có giới hạn và khó bổ sung đột ngột.
- Không có thời gian đọc báo cáo tài chính dài.
- Cần hiểu thông tin trên màn hình nhỏ trong vài giây.
- Trạng thái phải rõ khi dùng ngoài trời hoặc khi khó phân biệt màu.

## JTBD

> Khi cân nhắc một khoản chi mới, tôi muốn biết ngân sách nào đang gần hết và số tiền còn lại để quyết định khoản chi đó có phù hợp hay không.

## Tình huống chính

Trước khi đi ăn cùng bạn, Thảo mở Home và thấy danh mục Ăn uống đã dùng 84,5% ngân sách. Nhãn "Sắp vượt ngân sách" xuất hiện cùng số tiền còn lại, icon và progress bar. Trong Budget Detail, Thảo xem các giao dịch liên quan và nhận ra mình đã ăn ngoài nhiều lần trong tuần. Thảo giữ nguyên hạn mức, nhưng quyết định giảm khoản chi này trong những ngày còn lại.

## Tiêu chí thành công

- Xác định danh mục có nguy cơ trong dưới 10 giây từ Home.
- Nói được số tiền còn lại và hiểu ý nghĩa cảnh báo.
- Mở được các giao dịch nguồn của danh mục.
- Hiểu số liệu mà không cần máy tính hoặc ứng dụng khác.
- Nhận biết trạng thái mà không phụ thuộc vào màu sắc.

## Hàm ý thiết kế

- Home ưu tiên số tiền còn lại và những danh mục cần chú ý.
- Budget card hiển thị spent, limit, remaining, percentage và status.
- Trạng thái warning và exceeded kết hợp icon, chữ, số liệu và màu.
- Budget Detail có lối sang danh sách giao dịch đã lọc và Insights.
- Biểu đồ luôn đi kèm phần tóm tắt bằng chữ.
- Nội dung dùng giọng trung tính và đưa ra bước tiếp theo cụ thể.
