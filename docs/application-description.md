# Mô tả ứng dụng Expense Tracker

## 1. Giới thiệu

Expense Tracker là ứng dụng di động hỗ trợ sinh viên sống xa nhà ghi nhận và kiểm soát chi tiêu cá nhân. Ứng dụng tập trung vào những thao tác người dùng cần thực hiện hằng ngày: thêm một khoản chi, xem ngân sách còn lại, tìm lại giao dịch và nhận biết danh mục nào có nguy cơ vượt hạn mức.

Ứng dụng không hướng tới việc thay thế ngân hàng, ví điện tử hoặc một hệ thống kế toán đầy đủ. Mục tiêu chính là giúp người dùng hình thành thói quen ghi nhận chi tiêu bằng một quy trình ngắn, dễ hiểu và không tạo cảm giác bị phán xét.

## 2. Bối cảnh vấn đề

Sinh viên sống xa gia đình thường nhận tiền sinh hoạt theo tháng nhưng phát sinh nhiều khoản chi nhỏ trong ngày như ăn uống, gửi xe, xăng, tài liệu học tập và mua sắm cá nhân. Các khoản này dễ bị quên hoặc chỉ được ghi lại sau nhiều ngày.

Khi dữ liệu không được cập nhật thường xuyên, người dùng khó biết:

- Tiền đã được sử dụng vào những mục đích nào.
- Danh mục nào đang chiếm phần lớn ngân sách.
- Số tiền còn có thể sử dụng trong phần còn lại của tháng.
- Một khoản chi mới sẽ ảnh hưởng như thế nào đến kế hoạch hiện tại.

Nhiều ứng dụng quản lý tài chính có quá nhiều chức năng, yêu cầu người dùng thiết lập phức tạp hoặc trình bày cảnh báo theo hướng tiêu cực. Điều này khiến người dùng mới dễ bỏ cuộc trước khi hình thành thói quen.

## 3. Giải pháp đề xuất

Expense Tracker cung cấp một quy trình đơn giản:

1. Người dùng đăng nhập bằng tài khoản Google.
2. Người dùng thêm khoản chi bằng số tiền, danh mục và ngày phát sinh.
3. Giao dịch mới được lưu và ngân sách liên quan được cập nhật.
4. Home Dashboard hiển thị tổng chi, ngân sách còn lại và giao dịch gần đây.
5. Khi một danh mục gần hoặc đã vượt hạn mức, ứng dụng giải thích trạng thái và cho phép xem các giao dịch tạo ra kết quả đó.
6. Người dùng xem Insights và xuất báo cáo PDF vào cuối tháng.

Vòng lặp giá trị chính của sản phẩm là:

> Ghi khoản chi -> ngân sách cập nhật -> hiểu xu hướng -> điều chỉnh hành vi -> xuất báo cáo.

## 4. Người dùng mục tiêu

Người dùng chính là sinh viên từ 18 đến 24 tuổi:

- Sống xa gia đình và tự quản lý tiền sinh hoạt.
- Nhận tiền theo tháng hoặc có thu nhập bán thời gian.
- Sử dụng điện thoại Android làm thiết bị chính.
- Có nhiều khoản chi nhỏ và không duy trì được thói quen ghi chép lâu dài.
- Muốn biết mình còn có thể chi bao nhiêu thay vì đọc báo cáo tài chính phức tạp.

Persona đại diện là Nguyễn Minh, 21 tuổi, sinh viên năm ba đang thực tập bán thời gian tại TP.HCM. Minh nhận 5.000.000 VND tiền sinh hoạt vào đầu tháng nhưng thường chỉ nhận ra ngân sách ăn uống sắp hết khi tháng gần kết thúc.

## 5. Mục tiêu sản phẩm

- Giảm thời gian cần thiết để ghi nhận một khoản chi.
- Giúp người dùng hiểu tình hình tài chính tháng ngay từ Home.
- Phát hiện sớm nguy cơ vượt ngân sách.
- Cho phép sửa lỗi và phục hồi thao tác xóa an toàn.
- Cung cấp báo cáo ngắn gọn và có thể xuất thành PDF.
- Chuẩn bị thiết kế rõ ràng để hiện thực bằng Flutter và Firebase trong Lab 3.

## 6. Giá trị mang lại

### Nhanh

Form thêm khoản chi chỉ yêu cầu ba thông tin bắt buộc: số tiền, danh mục và ngày. Người dùng có thể hoàn thành thao tác mà không cần đi qua nhiều bước.

### Dễ hiểu

Home ưu tiên các câu hỏi thực tế: tháng này đã chi bao nhiêu, còn bao nhiêu và danh mục nào cần chú ý. Biểu đồ luôn có phần mô tả bằng văn bản.

### Có thể phục hồi

Form giữ lại dữ liệu khi validation hoặc lỗi mạng. Xóa giao dịch cần xác nhận và có hành động Undo.

### Không phán xét

Thông báo sử dụng ngôn ngữ trung tính. Ứng dụng giải thích dữ liệu và đề xuất bước tiếp theo thay vì đánh giá hành vi của người dùng.

### Riêng tư

Dữ liệu thuộc về tài khoản đã đăng nhập. Thiết kế chuẩn bị cho việc giới hạn dữ liệu theo từng người dùng bằng Firebase Authentication và Firestore Security Rules trong Lab 3.

## 7. Chức năng chính

### Đăng nhập và hồ sơ

- Đăng nhập bằng Google.
- Hiển thị ảnh đại diện, tên và email.
- Đăng xuất khỏi ứng dụng.

### Home Dashboard

- Tổng chi trong tháng.
- Ngân sách còn lại.
- Tiến độ sử dụng ngân sách.
- Các danh mục chi nhiều nhất.
- Giao dịch gần đây.
- Cảnh báo cần chú ý.

### Quản lý giao dịch

- Xem danh sách giao dịch.
- Tìm kiếm, lọc và sắp xếp.
- Thêm, xem, chỉnh sửa và xóa khoản chi.
- Xác nhận trước khi xóa.
- Hoàn tác sau khi xóa.

### Quản lý ngân sách

- Tạo hạn mức tháng theo danh mục.
- Chỉnh sửa hạn mức và ngưỡng cảnh báo.
- Xem số đã chi, còn lại và phần trăm sử dụng.
- Phân biệt trạng thái an toàn, sắp đạt ngưỡng và vượt hạn mức.
- Xem các giao dịch đóng góp vào ngân sách.

### Insights

- Xem tổng chi theo tháng.
- Xem phân bổ theo danh mục.
- Đọc tóm tắt bằng văn bản thay cho biểu đồ.
- Mở danh sách giao dịch nguồn.

### Báo cáo PDF

- Chọn tháng cần xuất.
- Tạo báo cáo gồm tổng quan, phân bổ danh mục và danh sách giao dịch.
- Theo dõi trạng thái đang xử lý, thành công hoặc thất bại.
- Mở báo cáo sau khi tạo thành công.

### Notification Center

- Hiển thị cảnh báo ngân sách.
- Phân biệt đã đọc và chưa đọc.
- Mở trực tiếp Budget Detail liên quan.

## 8. Cấu trúc điều hướng

Ứng dụng có bốn khu vực chính trong Bottom Navigation:

1. **Home:** Tổng quan tài chính tháng và hành động tiếp theo.
2. **Giao dịch:** Danh sách và quản lý các khoản chi.
3. **Ngân sách:** Theo dõi và thiết lập hạn mức.
4. **Hồ sơ:** Thông tin người dùng, thông báo, báo cáo và đăng xuất.

Hành động `Thêm khoản chi` được đặt nổi bật trên Home và Transaction List vì đây là thao tác thường xuyên nhất.

## 9. Các luồng sử dụng chính

### Luồng 1 - Thêm khoản chi

Người dùng bắt đầu tại Home, mở form thêm khoản chi, nhập dữ liệu và lưu. Nếu dữ liệu không hợp lệ, lỗi được hiển thị gần trường nhập. Nếu kết nối bị gián đoạn, dữ liệu vẫn được giữ để người dùng thử lại. Khi lưu thành công, người dùng xem Transaction Detail và Home hiển thị ngân sách mới.

### Luồng 2 - Chỉnh sửa hoặc xóa giao dịch

Người dùng mở một giao dịch từ Transaction List. Người dùng có thể chỉnh sửa rồi lưu lại, hoặc chọn xóa. Thao tác xóa cần được xác nhận. Sau khi xóa, Snackbar cung cấp hành động Undo để khôi phục.

### Luồng 3 - Kiểm soát ngân sách và xuất báo cáo

Người dùng mở Budget Detail để xem tiến độ và các giao dịch liên quan. Người dùng có thể điều chỉnh hạn mức, chuyển sang Insights và tạo báo cáo PDF. Nếu quá trình tạo hoặc tải báo cáo thất bại, ứng dụng hiển thị nguyên nhân và cho phép thử lại.

## 10. Danh sách màn hình

| ID | Màn hình | Vai trò |
| --- | --- | --- |
| AU-01 | Login | Đăng nhập Google |
| HM-01 | Home Dashboard | Tổng quan tháng |
| TX-01 | Transaction List | Danh sách giao dịch |
| TX-02 | Add/Edit Expense | Thêm hoặc sửa khoản chi |
| TX-03 | Transaction Detail | Chi tiết giao dịch |
| BD-01 | Budget Dashboard | Tổng quan ngân sách |
| BD-02 | Budget Detail | Chi tiết và nguyên nhân |
| BD-03 | Create/Edit Budget | Tạo hoặc sửa ngân sách |
| IN-01 | Insights | Phân tích chi tiêu |
| EX-01 | Export Report | Xuất báo cáo PDF |
| NT-01 | Notification Center | Cảnh báo ngân sách |
| ST-01 | Profile | Hồ sơ và cài đặt |

## 11. Trạng thái trải nghiệm

Các màn hình có dữ liệu từ mạng cần thể hiện rõ:

- **Loading:** Skeleton theo cấu trúc nội dung thật.
- **Empty:** Giải thích chưa có dữ liệu và cung cấp hành động phù hợp.
- **Error:** Nêu nguyên nhân dễ hiểu và có nút thử lại.
- **Offline:** Cho biết dữ liệu có thể chưa mới và thao tác nào chưa đồng bộ.
- **Success:** Xác nhận kết quả và cung cấp hành động tiếp theo.

Form phải giữ dữ liệu đã nhập khi xảy ra validation error hoặc network error.

## 12. Nguyên tắc giao diện

- Giao diện đơn giản, bình tĩnh và đáng tin cậy.
- Mỗi màn hình có một hành động chính.
- Số tiền và trạng thái ngân sách có thứ bậc thị giác rõ ràng.
- Cảnh báo luôn có nguyên nhân và bước tiếp theo.
- Không truyền đạt trạng thái chỉ bằng màu sắc.
- Touch target tối thiểu 48 x 48 dp.
- Body text tối thiểu 14 sp.
- Thiết kế chính ở 360 x 800 dp và kiểm tra thêm chiều rộng 412 dp.

## 13. Phạm vi không thực hiện

Phiên bản Lab 2 không thiết kế sâu và Lab 3 không dự kiến triển khai:

- OCR hóa đơn và xử lý camera.
- Đồng bộ tài khoản ngân hàng hoặc ví điện tử.
- Thanh toán hoặc chuyển tiền.
- Quản lý chi phí nhóm và mạng xã hội.
- AI tư vấn tài chính.
- Quản lý đầu tư, khoản vay và tài sản.
- Hệ thống subscription trả phí.
- iOS và web admin.

Việc giới hạn phạm vi giúp toàn bộ màn hình trong Lab 2 có thể được hiện thực đầy đủ bằng Flutter và Firebase trong Lab 3.

## 14. Tiêu chí thành công

- Người dùng thêm khoản chi và thấy ngân sách cập nhật trong dưới 20 giây.
- Người dùng xác định danh mục cần chú ý trong dưới 10 giây từ Home.
- Ba user flow có thể hoàn thành từ đầu đến cuối mà không có ngõ cụt.
- Người dùng có thể phục hồi sau lỗi nhập liệu, lỗi mạng và thao tác xóa nhầm.
- Giao diện đáp ứng yêu cầu accessibility và responsive của Lab 2.

## 15. Hướng phát triển trong Lab 3

Thiết kế này được chuẩn bị để triển khai bằng:

- Flutter và Dart cho ứng dụng Android.
- MVVM với Provider hoặc Riverpod.
- Firebase Authentication cho Google Sign-In.
- Cloud Firestore cho giao dịch, ngân sách, thông báo và metadata báo cáo.
- Firebase Cloud Messaging cho cảnh báo.
- Remote Config cho giới hạn hoặc nội dung có thể thay đổi.
- Crashlytics và Analytics để theo dõi chất lượng và hành vi.
- Dịch vụ object storage để lưu báo cáo PDF.

