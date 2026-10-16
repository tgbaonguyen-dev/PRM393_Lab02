# Scenarios, quyết định UI và kế hoạch test

2026-10-15 · Kế hoạch thiết kế/kiểm chứng, **chưa phải kết quả test với người dùng**. [Persona](persona.md) · [Nguồn, coverage và assumptions](discovery-and-evidence.md).

## SC01 — Ghi khoản chi ngay sau thanh toán

- **Persona:** P01 Primary; P02/P03 cũng có thể thực hiện.
- **Trigger/bối cảnh:** vừa trả một khoản ăn uống, còn nhớ số tiền; chú ý ngắn, có thể dùng một tay. Đây là tình huống giả định.
- **Mục tiêu:** ghi đúng khoản chi và biết ngân sách thay đổi thế nào trước khi rời app.
- **Điều kiện đầu:** đã đăng nhập; HM-01 có kỳ/ngân sách và số liệu mẫu đã xác định. Dữ liệu test không phải dữ liệu riêng tư.
- **Task:** từ HM-01 mở TX-02, ghi số tiền/danh mục/ngày theo đề, lưu, kiểm tra TX-03 và Home cập nhật.
- **Kết quả mong đợi:** đúng một transaction mới; tiền tổng tăng đúng amount; remaining của đúng category/kỳ giảm tương ứng; có feedback Saving → result.
- **Nhánh thay thế/phục hồi:** amount không hợp lệ có lỗi gần field; lỗi lưu giữ dữ liệu và Retry không tạo trùng. Đây là thiết kế cần xác minh, không bảo đảm runtime đã đạt.
- **Success:** target <20 giây từ thao tác mở Add Expense tới khi người dùng nhận biết ngân sách cập nhật, không hướng dẫn; correctness phải đạt độc lập với thời gian. Xem T01/T02.
- **Giới hạn hiện tại:** prototype sử dụng prepared values; không đo khả năng nhập tự do hoặc thời gian thực hiện sản phẩm bằng việc bấm một hotspot điền sẵn.

## SC02 — Hiểu cảnh báo và điều chỉnh có căn cứ

- **Persona:** P02 Secondary; Primary vẫn cần hiểu cảnh báo.
- **Trigger/bối cảnh:** chuẩn bị chi tiếp hoặc thấy cảnh báo danh mục; cần cân nhắc còn bao nhiêu. Chưa quan sát sinh viên thật trong bối cảnh này.
- **Mục tiêu:** hiểu danh mục cần chú ý, số còn lại và nguyên nhân, rồi giữ hoặc điều chỉnh kế hoạch một cách có chủ đích.
- **Điều kiện đầu:** HM-01/BD-01 có state warning và dữ liệu kỳ rõ; NT-01 → BD-02 là entry thay thế.
- **Task:** chỉ ra danh mục cần chú ý từ Home; vào BD-02, giải thích remaining/percent và giao dịch đóng góp; nếu task yêu cầu sửa, vào BD-03 và lưu giới hạn hợp lệ.
- **Kết quả mong đợi:** người dùng đọc đúng ý nghĩa cảnh báo; không phải tăng hạn mức mới được tiếp tục. Khi chọn sửa, dùng fixture đã có trong Flow 3: spent 1.800.000, limit 2.500.000 → remaining 700.000 và 72%. Fixture không phải thu nhập/số dư thực tế của Thảo.
- **Nhánh thay thế/phục hồi:** xem giao dịch nguồn ở TX-01 filtered; giữ nguyên limit; hủy sửa; giá trị limit/threshold không hợp lệ không được ghi. Back theo nguồn và network Retry cần kiểm riêng.
- **Success:** nhận ra đúng category <10 giây từ Home (target PRD); giải thích được ít nhất remaining và nguồn chi; số sau sửa khớp fixture. Xem T03/T04.
- **Giới hạn:** prototype Back đã có lỗi trong rehearsal trước; hiểu cảnh báo và các target thời gian chưa được test với người dùng.

## SC03 — Rà soát, sửa sai và mở báo cáo

- **Persona:** P03 Secondary; đây là giả thuyết hành vi rà soát, không phải user role mới.
- **Trigger/bối cảnh:** lúc rà soát cuối kỳ, thấy một khoản có vẻ trùng hoặc sai danh mục. Chưa có cuộc phỏng vấn xác nhận tình huống.
- **Mục tiêu:** truy đúng nguồn, sửa dữ liệu an toàn và biết mình đang xem báo cáo của kỳ nào.
- **Điều kiện đầu:** test dataset có giao dịch mục tiêu, bản đối chiếu chuẩn và tổng trước/sau rõ ràng; không tự xem hai khoản giống nhau là duplicate nếu task không xác nhận.
- **Task:** từ TX-01 tìm đúng khoản, mở TX-03, sửa tại TX-02 hoặc chọn xóa; thử Cancel và Undo theo các trial tách biệt; sau đó vào IN-01 và EX-01 chọn đúng tháng, chờ Ready, mở preview.
- **Kết quả mong đợi:** chỉ giao dịch được chọn thay đổi; Cancel không đổi dữ liệu; Undo khôi phục một lần; tổng/remaining tính đúng; tên kỳ và state report rõ.
- **Nhánh thay thế/phục hồi:** không có kết quả lọc giải thích được trạng thái; lỗi lưu giữ context; export failed cho phép Retry đúng kỳ đã chọn. Các state có trong đặc tả, nhưng không mặc định đã hoạt động thật.
- **Success:** chọn/sửa đúng khoản, không thao tác nhầm khoản khác, giải thích đúng tổng và kỳ báo cáo; không đặt thêm ngưỡng thời gian tùy ý. Xem T05–T07.
- **Giới hạn:** PDF hiện là preview mô phỏng; data consistency, search/filter/edit thật không suy ra từ số liệu đã điền sẵn.

## Ma trận Persona → Need → UI decision → Test

Nxx là nhãn nhu cầu trong ma trận này. D01–D10 là alias của **10 quyết định đã có** trong [design-decisions.md](../design/design-decisions.md), không phải quyết định lịch sử mới.

| Persona / Need | Kết quả người dùng muốn | Giả thuyết/quyết định UI hiện có | Flow / screens | Test | Nguồn và assumption |
| --- | --- | --- | --- | --- | --- |
| P01 · N01 | Ghi đúng trước khi quên | D02 FAB, D03 form một màn hình | Flow 1; HM-01/TX-02/TX-03 | T01 | R01–R04; A01 |
| P01 · N02 | Không nhập lại hoặc ghi trùng sau lỗi | D04 lỗi gần field, giữ input | Flow 1; TX-02 states | T02 | R04/R05; A02 |
| P02 · N03 | Biết danh mục cần chú ý và ý nghĩa số còn lại | D06 status đa tín hiệu, D07 ngôn ngữ trung tính | Flow 3; HM-01/BD-01/BD-02/NT-01 | T03 | R01/R05/R06; A03/A04 |
| P02 · N04 | Điều chỉnh dựa trên nguyên nhân, không che vượt chi | D08 text summary/drill-down; BD-02 → TX-01/BD-03 | Flow 3 | T04 | R04/R05; A03 |
| P03 · N05 | Sửa sai và có thể đổi ý khi xóa | D05 confirmation + Undo; TX detail/edit hiện có | Flow 2; TX-01/TX-02/TX-03 | T05/T06 | R01/R04/R05; A05 |
| P03 · N06 | Tin số tổng và biết đúng kỳ báo cáo | D08 summary + nguồn; FR-06 report states | Flow 3; IN-01/EX-01 | T07 | R01/R05; A06 |
| Tất cả · N07 | Đọc và thao tác không bị loại trừ | D06 + accessibility/responsive rules | Cả ba flow | T08 | R05/R06; A07 |

UI decision là giải pháp để thử, không được đổi tên thành user need đã xác thực. Một need có thể có nhiều giải pháp; task test phải kiểm tra cả khả năng hiểu và correctness, không chỉ “có nút”.

## Kế hoạch test

Mọi hàng dưới đây có status **Planned / chưa thực hiện**. Txx là test case, không phải bằng chứng đã pass. Functional checks của prototype và nghiên cứu usability phải được lưu riêng.

| ID | Persona / task | Kiểm tra và tiêu chí | Bằng chứng cần lưu | Trạng thái |
| --- | --- | --- | --- | --- |
| T01 | P01 thêm khoản chi | Đúng amount/category/date, một bản ghi, tổng/remaining đúng; target <20s không trợ giúp; thời gian prototype điền sẵn ghi riêng | Dữ liệu trước/sau, thời điểm start/end, lỗi/trợ giúp, note ẩn danh và phiên bản prototype | Planned |
| T02 | P01 sửa amount sai hoặc mất kết nối | Field message rõ; input còn; Retry không duplicate; người dùng biết lưu đã thành công chưa | Trace state/action, dữ liệu chuẩn và clip được đồng ý; không gọi thiết kế tĩnh là runtime pass | Planned |
| T03 | P02 nhận diện warning | Đúng category <10s từ Home, nói được remaining và nghĩa warning không cần dựa duy nhất vào màu | Task wording, time, câu trả lời đúng/sai, hỗ trợ đã dùng | Planned |
| T04 | P02 xem nguồn và sửa limit | Xem được giao dịch đóng góp; giữ limit cũng là lựa chọn; fixture spent 1,8m/limit 2,5m cho 72%/700k; hủy không đổi | Snapshot dataset, thao tác, câu giải thích, Back destinations thực tế | Planned |
| T05 | P03 tìm/sửa giao dịch | Chọn đúng khoản khi có các khoản tương tự; edit đúng field, không đổi khoản khác, tổng/remaining đúng | Bản đối chiếu, giao dịch mục tiêu, trạng thái trước/sau, lỗi và assistance | Planned |
| T06 | P03 Cancel/xóa/Undo | Cancel giữ nguyên; confirm chỉ xóa khoản chọn; Undo khôi phục đúng một lần và tổng đúng | Hai trial độc lập, overlay/actions, dữ liệu chuẩn | Planned |
| T07 | P03 Insights/PDF | Đúng kỳ và số chuẩn; nhận biết processing/ready/failed; Retry giữ kỳ; mở preview. Test tạo/tải PDF thật chỉ khi có backend | Kỳ/dataset, state transitions, PDF-preview versus real-file note, known Back defect | Planned |
| T08 | Tất cả; đọc và chạm | Actual body ≥14sp; hit area ≥48×48dp; contrast phù hợp; không chỉ dùng màu; reflow 360/412dp và tăng chữ không mất nội dung chính | Layer bounds/text properties, contrast pairs, device/frame width, text-scale setting và ảnh kết quả | Planned; audit token riêng đã có |

Không suy ra T01/T03 đạt từ target được viết trên slide. Không lấy số token contrast đạt để đánh dấu T08 hoàn thành. Không đánh dấu T07 export thật đạt bằng PDF preview.

## Quy tắc ghi kết quả sau này

Mỗi run cần test ID, ngày, phiên bản artifact, participant ID ẩn danh (nếu có), dataset, hành động, kết quả mong đợi/thực tế, pass/fail/blocked, mức trợ giúp và đường dẫn bằng chứng. Ghi cả thất bại; test chưa chạy không được tính pass. Chỉ gắn E-ID cho bằng chứng người dùng thực sự thu thập và được phép sử dụng.
