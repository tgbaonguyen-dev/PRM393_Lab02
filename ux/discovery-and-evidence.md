# Discovery và bằng chứng — Expense Tracker

Ngày bổ sung: 2026-10-15. **Desk review từ dự án hiện có, không phải workshop hay nghiên cứu đã thực hiện.** Đọc cùng [ba Proto-Persona](persona.md).

## 1. Sổ nguồn và ranh giới bằng chứng

| Ref | Nguồn | Xác nhận được | Không chứng minh được |
| --- | --- | --- | --- |
| R01 | [Product requirements](../requirements/EXPENSE_TRACKER_REQUIREMENTS.md), mục 1–7 | Target 18–24 tuổi/Android; FR-01…FR-07; MVP và out-of-scope | Tần suất, nhu cầu hay động lực của sinh viên thật |
| R02 | [README — Tổng quan sản phẩm](../README.md#tổng-quan-sản-phẩm) | Value loop, chức năng, targets <20s và <10s | Mục tiêu đã đạt hoặc phân khúc đã xác thực |
| R03 | [AI design log](../ai/ai-design-log.md), initial generation | Prompt gốc dùng Minh với bối cảnh 5 triệu/tháng và phiên ngắn | Tiểu sử Minh là dữ liệu phỏng vấn; Thảo/Huy tham gia prompt cũ |
| R04 | [User flow](user-flow.md), mục 3–7 | Ba flow thiết kế và nhánh thay thế/phục hồi | Toàn bộ tương tác Figma thực sự chạy đúng |
| R05 | [Screen specs](../design/screen-spec.md) | Screen ID, nội dung, validation, states và đích điều hướng trong đặc tả | Search/filter/edit/backend/PDF hoạt động thật |
| R06 | [Design decisions](../design/design-decisions.md), quyết định 1–10 | Những quyết định đã được ghi lại trước lần bổ sung persona | Quyết định đó được người dùng mới xác nhận |
| R07 | [Persona guideline](https://prm393-material.web.app/persona-guideline), mục 2–8; [Chuẩn chung](https://prm393-material.web.app/#standards) | 12 trường, phân loại bằng chứng, artifact và ngưỡng tự kiểm | Điểm chính thức của bài hay xác nhận nhóm đã đạt 80 |

R là mã tham chiếu tài liệu, **không phải E-ID nghiên cứu người dùng**. Chưa có bản ghi Observed/Reported từ người tham gia trong gói bổ sung này. Quan sát prototype chỉ là kiểm chứng phần mềm, không chứng minh một persona đại diện người dùng thật.

## 2. User/Stakeholder Map — bản đề xuất

```text
Sinh viên tự quản lý chi tiêu cá nhân trên Android
├── P01: ghi ngay, ít thời gian/chú ý
├── P02: kiểm soát giới hạn trước khi chi
└── P03: rà soát dữ liệu theo đợt
     Cùng một người có thể thể hiện nhiều hành vi; chưa chứng minh ba phân khúc độc lập.

Nhóm ảnh hưởng / stakeholder, không tự động thành persona app
├── Gia đình: có thể cấp tiền sinh hoạt; không có tài khoản xem tiền con trong MVP
├── Nhóm thiết kế/phát triển: tạo UI, kiểm thử, handoff; không có admin app riêng
└── Giảng viên: đánh giá artifact và prototype; không phải end-user persona

Ngoài phạm vi
└── Ngân hàng, ví điện tử, nhóm chia tiền, phụ huynh giám sát, kế toán doanh nghiệp
     Không đồng bộ, thanh toán, phân quyền nhóm hay báo cáo kế toán mới.
```

Người có thể bị bỏ sót cần tuyển/kiểm tra: người mới ghi chi; người quen ghi chi; thiết bị Android nhỏ/cũ; người dùng tăng chữ hoặc gặp hạn chế thao tác; kết nối không ổn định. Không gán một khuyết tật hay hoàn cảnh cho tên persona nếu chưa có bằng chứng. Phần tuyển là kế hoạch, chưa có người tham gia.

## 3. Board tổng hợp giả định từ tài liệu — chưa phải Affinity Board nghiên cứu

Mỗi hàng là một **thẻ seed do desk review**, dẫn nguồn phạm vi và assumption ID. Không ghi thành câu người dùng đã nói; không dùng ảnh board dựng sau để giả làm workshop đã diễn ra.

| Card | Nội dung seed | Nguồn tài liệu | Giả định cần kiểm | Cụm tạm |
| --- | --- | --- | --- | --- |
| C01 | Nhiều khoản nhỏ bị quên nếu không ghi ngay | R01 target user; R03 prompt | A01 | Ghi ngay |
| C02 | Form ngắn giảm cản trở ghi trong phiên ngắn | R05 TX-02; R06 D03 | A01, A02 | Ghi ngay |
| C03 | Nhập lại sau lỗi làm bỏ dở | R04 Flow 1; R06 D04 | A02 | Phục hồi xuyên cụm |
| C04 | Tổng chi chưa đủ để quyết định khoản chi kế tiếp | R01 FR-02/04; R02 mục 6 | A03 | Kiểm soát hạn mức |
| C05 | Cần truy nguồn gây cảnh báo trước khi sửa kế hoạch | R05 BD-02/TX-01; R06 D08 | A03 | Kiểm soát hạn mức |
| C06 | Cảnh báo trung tính, có chữ và icon dễ diễn giải hơn | R01 mục 9; R06 D06/D07 | A04, A07 | Kiểm soát + accessibility |
| C07 | Khi tổng không khớp, cần tìm và sửa khoản cũ | R01 FR-03; R04 Flow 2 | A05 | Rà soát độ đúng |
| C08 | Cancel/Undo hỗ trợ tin tưởng thao tác xóa | R06 D05 | A05 | Rà soát + phục hồi |
| C09 | Bản tổng hợp tháng có thể hỗ trợ rà soát | R01 FR-05/06; R05 IN-01/EX-01 | A06 | Rà soát cuối kỳ |

**Giải thích phân nhóm:** P01 ưu tiên công ghi ngay; P02 ưu tiên ra quyết định trước/ngay khi chi; P03 ưu tiên tin số liệu sau khi đã ghi. Nhóm theo kết quả, thời điểm và rào cản, không theo tuổi/giới. Error recovery và accessibility là nhu cầu xuyên cụm, không dùng riêng để “vẽ đủ” một persona nữa.

Sau nghiên cứu: thay seed bằng note có E-ID, gắn Observed/Reported/Inferred/Assumed, lưu cả dữ liệu phản ví dụ và phiên bản board. Hiện chưa có workshop/ảnh brainstorming thật; không đánh dấu đầu ra đó đã hoàn thành.

### Ranh giới giả thuyết và điều kiện giữ/gộp

Bảng này giải thích **đề xuất phân nhóm**, không phải pattern đã quan sát. Chỉ khác thời điểm sử dụng chưa đủ để giữ persona riêng.

| Giả thuyết | Trigger → kết quả ưu tiên | Hệ quả UI và cách kiểm | Điều kiện xem xét lại |
| --- | --- | --- | --- |
| P01 · A01/A02 | Vừa thanh toán → ghi đúng trước khi quên | N01/N02: entry dễ thấy, form ngắn, giữ input; D02–D04; T01/T02 | Nếu chủ yếu ghi theo đợt, giảm ưu tiên tốc độ tức thời; cân nhắc gộp P03 |
| P02 · A03/A04 | Trước khi chi/có cảnh báo → quyết định dựa trên remaining và nguyên nhân | N03/N04: remaining, trạng thái và giao dịch nguồn; D06–D08; T03/T04 | Nếu không có mục tiêu/rào cản riêng ngoài xem tổng, giữ như scenario thay vì persona độc lập |
| P03 · A05 | Tổng không khớp → giải thích và sửa để tin dữ liệu | N05/N06: nhận diện khoản, sửa/Cancel/Undo, đúng kỳ; D05/D08; T05–T07 | Nếu cùng mục tiêu/rào cản với P01, gộp; không giữ riêng chỉ vì dùng cuối tháng hoặc có màn PDF |

**Ranh giới yếu nhất: P01–P03.** Chỉ giữ riêng nếu dữ liệu thật cho thấy khác biệt lặp lại về ưu tiên và rào cản dẫn tới hệ quả thiết kế khác. Kiểm cùng ba task với mọi người và tìm phản ví dụ trước khi kết luận. Accessibility và recovery vẫn là yêu cầu xuyên nhóm dù gộp persona.

## 4. Persona Coverage Matrix và đối chiếu dự án

| Persona | Kết quả ưu tiên / rào cản | FR và flow hiện có | Screen IDs đã có trong spec | Khác biệt review UI | Giới hạn xác minh |
| --- | --- | --- | --- | --- | --- |
| P01 | Ghi đúng ngay; ít chú ý, dễ bỏ nhập | FR-02/03; Flow 1, có dùng Flow 2 | HM-01, TX-02, TX-03 | FAB dễ thấy; 3 field bắt buộc; saving/validation/giữ input | <20s là target; prototype nhập giá trị mẫu, không phải test nhập tự do |
| P02 | Hiểu danh mục cần chú ý và nguyên nhân | FR-02/04/05/07; Flow 3 | HM-01, BD-01, BD-02, BD-03, NT-01, TX-01, IN-01 | Remaining + percent + nhãn; nguồn chi; điều chỉnh là lựa chọn, không ép tăng | <10s và hiểu cảnh báo chưa đo; Back còn lỗi; warning token chưa đạt contrast chữ thường |
| P03 | Rà soát, sửa, khôi phục và tổng hợp | FR-03/05/06; Flow 2 + Flow 3 | TX-01, TX-02, TX-03, IN-01, EX-01; ST-01 là entry phụ | Nhận diện đúng khoản; edit/cancel/Undo rõ; kỳ và trạng thái report rõ | Search/filter/edit và tính đúng dữ liệu cần test riêng; PDF là preview mô phỏng |

AU-01 và ST-01 là chức năng nền dùng chung, không cần persona đăng nhập/admin mới. Personas không bị khóa vào một flow; bảng ghi nhiệm vụ ưu tiên, không độc quyền chức năng. Tổng số màn hình và flow không tăng.

### Nếu bỏ từng persona thì mất gì?

- Bỏ P01: dễ tối ưu báo cáo nhưng làm ghi chi hằng ngày quá tốn công.
- Bỏ P02: có số tổng nhưng khó giải thích cảnh báo hoặc quyết định trước khi chi.
- Bỏ P03: có thể xem số đẹp nhưng thiếu câu hỏi về truy vết, sửa sai và tin báo cáo.

Các khác biệt này có ích cho review ở mức giả thuyết. Nếu nghiên cứu không tìm thấy pattern tách biệt, gộp chúng lại thay vì giữ số lượng ba bằng mọi giá.

## 5. Assumption & Research Backlog

| ID | Giả định chưa kiểm chứng | Liên quan | Rủi ro nếu sai | Cách xác minh / dấu hiệu cần sửa |
| --- | --- | --- | --- | --- |
| A01 | Ghi ngay sau thanh toán và phiên ngắn là cản trở trọng tâm | P01, C01/C02 | Ưu tiên tốc độ sai vấn đề | Kể lại lần thanh toán gần nhất; quan sát cách ghi hiện tại; nếu chủ yếu ghi theo đợt, giảm ưu tiên P01 hoặc gộp P03 |
| A02 | Giữ input và feedback giúp hoàn thành thay vì bỏ dở | P01, xuyên cụm | Thiết kế recovery không đúng nguyên nhân | Quan sát lỗi có kiểm soát, kiểm tra dữ liệu giữ nguyên và người dùng hiểu trạng thái; không gây lỗi trên dữ liệu thật |
| A03 | Remaining và giao dịch nguồn giúp ra quyết định ngân sách | P02 | Cảnh báo nhiều thông tin nhưng không hành động được | Task hiểu cảnh báo, hỏi lý do giữ/sửa hạn mức; nếu chỉ cần remaining, đơn giản hóa UI |
| A04 | Cảnh báo không phán xét giảm bỏ qua | P02, xuyên cụm | Nhóm suy diễn động lực | Hỏi trải nghiệm thật với thông báo, so sánh cách người dùng diễn giải các câu; không hỏi dẫn “bạn có thích…?” |
| A05 | Có pattern rà soát riêng, cần tìm/sửa/Undo | P03 | P03 chỉ là tình huống khác của P01 | Tìm ví dụ sai lệch thực tế, tần suất và công cụ; gộp nếu không có mục tiêu/rào cản khác |
| A06 | PDF hữu ích cho tự rà soát cuối kỳ | P03 | Persona bị dựng để hợp thức hóa FR-06 | Hỏi lần dùng báo cáo gần nhất và đầu ra muốn giữ; nếu không cần, vẫn ghi là yêu cầu lab/feature, không gọi nhu cầu đã xác thực |
| A07 | Nhãn, contrast, text scaling và hit areas đáp ứng người dùng | Tất cả | Loại trừ người dùng/không hoàn thành task | Audit frame, thiết bị 360/412dp, tăng chữ; token contrast không thay audit; ghi kết quả pass/fail thật |
| A08 | Ba cụm đủ khác nhau và đủ bao phủ target | Tất cả | Chia persona theo feature thay vì hành vi | Interview cross-task, affinity có phản ví dụ, xem người dùng có chuyển cụm; tách/gộp và sửa priority nếu cần |

Ưu tiên xác minh A01/A03/A05/A08 trước khi gọi đây là phân khúc. Kiểm tra A07 song song vì liên quan khả năng dùng, không chờ đủ persona. Không có deadline/kết quả giả hay mã bằng chứng đã thu thập cho các hàng này.
