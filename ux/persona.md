# QUẢN LÝ CHI TIÊU & NHẬT KÝ MUA SẮM

## _Quản lý chi tiêu, lưu giữ khoảnh khắc mua sắm_

Đây là ứng dụng quản lý tài chính cá nhân kết hợp nhật ký mua sắm, được thiết kế theo hướng mobile-first cho cá nhân, cặp đôi và gia đình. Ứng dụng giúp người dùng ghi nhận một khoản chi ngay tại thời điểm mua hàng, hiểu tác động của khoản chi đó đến ngân sách và lưu lại hoá đơn, món đồ cùng câu chuyện liên quan trong một nơi.

Thay vì chỉ hiển thị những con số khô khan, ứng dụng biến mỗi giao dịch thành một **khoảnh khắc chi tiêu có ngữ cảnh**: người dùng đã mua gì, ở đâu, cùng ai, bằng nguồn tiền nào và vì sao khoản chi đó có ý nghĩa.

> Chụp để ghi nhận. Hiểu để kiểm soát. Lưu lại để luôn tìm thấy khi cần.

---

# 1. Vấn đề ứng dụng giải quyết

Việc quản lý tài chính thường bị phân tán giữa ứng dụng ngân hàng, bảng tính, ảnh chụp hoá đơn, ghi chú và trí nhớ của người dùng. Một giao dịch có thể xuất hiện trong lịch sử thanh toán nhưng không cho biết món đồ nào đã được mua, còn ảnh hoá đơn lại khó tìm khi cần đổi trả hoặc bảo hành.

Các ứng dụng tài chính truyền thống cũng thường yêu cầu nhập liệu thủ công, tập trung quá nhiều vào báo cáo và dễ tạo cảm giác áp lực khi người dùng chi tiêu ngoài kế hoạch.

Ứng dụng kết nối các mảnh thông tin này thành một trải nghiệm liền mạch:

- Ghi nhận giao dịch nhanh bằng camera hoặc nhập thủ công.
- Trích xuất dữ liệu từ hoá đơn nhưng luôn để người dùng kiểm tra và xác nhận.
- Cập nhật ngân sách ngay sau khi giao dịch được lưu.
- Liên kết khoản chi với ảnh món đồ, chứng từ, bảo hành và hạn đổi trả.
- Chia sẻ khoảnh khắc hoặc chi phí với người thân trong phạm vi riêng tư do người dùng kiểm soát.

---

# 2. Ý tưởng cốt lõi

Camera là điểm vào trung tâm của ứng dụng. Người dùng có thể chụp hoá đơn, món đồ, chuyến mua sắm hoặc một khoảnh khắc ngay khi nó xảy ra. Ứng dụng xử lý ảnh trong nền, nhận diện các thông tin quan trọng và chỉ yêu cầu người dùng kiểm tra những trường chưa chắc chắn.

Vòng lặp giá trị chính của sản phẩm là:

$$\textbf{Chụp} \longrightarrow \textbf{Hiểu} \longrightarrow \textbf{Kiểm soát} \longrightarrow \textbf{Nhớ lại}$$

1. **Chụp:** Ghi nhận hoá đơn hoặc món đồ trong vài giây.
2. **Hiểu:** OCR đề xuất merchant, ngày, tổng tiền và các dòng hàng để người dùng xác nhận.
3. **Kiểm soát:** Giao dịch cập nhật ngân sách, báo cáo và kế hoạch tài chính.
4. **Nhớ lại:** Ảnh, hoá đơn và thông tin sau mua được lưu trong bộ sưu tập để tìm lại khi cần.

---

# 3. Người dùng mục tiêu & Chân dung Persona

### 3.1. Các nhóm người dùng chính

| Nhóm người dùng                | Nhu cầu chính                                  | Giải pháp hỗ trợ                                        |
| :----------------------------- | :--------------------------------------------- | :------------------------------------------------------ |
| **Người mới đi làm**           | Theo dõi chi tiêu và tránh vượt ngân sách      | Nhập nhanh, ngân sách đơn giản và cảnh báo sớm          |
| **Cặp đôi**                    | Quản lý chi phí chung nhưng vẫn giữ phần riêng | Chia hoá đơn, vòng tròn riêng tư và quyền xem linh hoạt |
| **Gia đình**                   | Theo dõi nhiều thành viên và chứng từ gia đình | Vai trò, hạn mức, lịch thanh toán và kho bảo hành       |
| **Người mua sắm thường xuyên** | Nhớ món đồ, hạn đổi trả và bảo hành            | Album món đồ, kho hoá đơn và lời nhắc sau mua           |
| **Freelancer**                 | Tách chi phí cá nhân và công việc              | Nhãn dự án, chứng từ, báo cáo và xuất dữ liệu           |

### 3.2. Chân dung Persona đại diện (Primary Persona)

- **Họ và tên:** Trần Quốc Tuấn
- **Độ tuổi:** 21 tuổi (Sinh viên năm 3 đại học công nghệ, sống tự lập tại phòng trọ)
- **Thu nhập / Trợ cấp:** 4.000.000 – 6.000.000 VNĐ / tháng (phụ cấp gia đình + làm thêm)

#### Bối cảnh hằng ngày (Daily Context)

- Lịch học và làm việc dày đặc, phát sinh nhiều khoản chi tiêu nhỏ lẻ hằng ngày (ăn trưa, gửi xe, cà phê chạy deadline, điện nước phòng trọ).
- Cuối ngày về mệt mỏi, không có thói quen mở sổ tay hoặc ứng dụng phức tạp ra gõ từng dòng. Thường giữ lại hoá đơn giấy trong ví nhưng quên không nhập.
- Khoảng ngày 20 – 25 hằng tháng là tài khoản báo động đỏ ("cháy túi") mà không rõ tiền đã đi đâu.

#### Thói quen sử dụng thiết bị

- **Thiết bị:** Smartphone Android tầm trung (màn hình 360 × 800 dp, RAM 4GB).
- **Môi trường sử dụng:** Thao tác nhanh tại quầy tính tiền hoặc lúc vừa nhận hóa đơn, dùng một tay (One-handed use).
- **Kết nối:** 4G đôi khi chập chờn khi ở trong các quán ăn hẻm sâu hoặc tầng hầm gửi xe.

#### Nỗi đau (Pain Points)

1. **Lười nhập liệu thủ công:** Các app tài chính hiện nay bắt chọn quá nhiều bước (ví, danh mục cha, danh mục con, ghi chú), tốn thời gian khiến nản sau vài ngày dùng.
2. **Quên chi tiêu tiền mặt:** Mua đồ nhận hoá đơn giấy thường vứt xó và quên mất.
3. **Thiếu cảnh báo sớm:** Chỉ nhận ra hết tiền khi số dư đã về 0, thiếu cảnh báo khi tốc độ tiêu tiền trong tuần vượt trần.

#### Mục tiêu (Goals)

1. Ghi lại chi tiêu cực nhanh ngay khi phát sinh (dưới 15 giây nếu nhập tay, hoặc 1 cú chụp ảnh hoá đơn).
2. Tự động kiểm soát không để chi tiêu vượt ngân sách tháng đã đặt ra.
3. Xem được bức tranh tài chính rõ ràng để biết mình đang tiêu lãng phí vào mục nào nhất.

---

# 4. Chức năng nổi bật

## Camera và OCR hoá đơn

Ứng dụng hỗ trợ chụp hoá đơn trực tiếp, nhập ảnh hoặc tài liệu có sẵn, tự động crop và cải thiện chất lượng ảnh. OCR nhận diện merchant, thời gian, tổng tiền, thuế, phí và từng dòng hàng. Mỗi kết quả đều có mức độ tin cậy để người dùng biết phần nào cần kiểm tra trước khi lưu.

## Giao dịch và tài khoản tiền

Người dùng có thể quản lý khoản thu, khoản chi, chuyển tiền, hoàn tiền và các tài khoản như tiền mặt, ngân hàng, thẻ hoặc ví điện tử. Giao dịch được gắn với danh mục, nhãn, merchant, địa điểm, người liên quan và chứng từ để có thể tìm kiếm hoặc đối soát về sau.

## Ngân sách và kế hoạch tài chính

Ứng dụng theo dõi số tiền đã chi, phần còn lại, tốc độ chi và nguy cơ vượt ngân sách. Thay vì phán xét, hệ thống giải thích nguyên nhân thay đổi và đưa ra những hành động nhỏ như điều chỉnh hạn mức, chuyển ngân sách hoặc ghi nhận một khoản ngoại lệ có chủ ý.

## Bộ sưu tập món đồ

Mỗi món đồ có thể được liên kết với giao dịch và dòng hàng trên hoá đơn. Người dùng lưu ảnh, thông tin sản phẩm, hạn đổi trả, bảo hành, lịch bảo trì và chi phí trong suốt vòng đời. Khi cần đổi trả hoặc bảo hành, toàn bộ chứng từ có thể được tìm thấy tại một nơi.

## Vòng tròn riêng tư và chi phí chung

Ứng dụng cho phép chia sẻ khoảnh khắc mua sắm với một người, một nhóm nhỏ hoặc hộ gia đình. Người dùng quyết định có hiển thị số tiền, merchant, địa điểm hay dòng hàng hay không. Với chi phí chung, các thành viên có thể chia từng món, xác nhận phần của mình và theo dõi trạng thái hoàn tiền.

## Báo cáo và trợ lý tài chính

Dashboard và báo cáo giúp người dùng hiểu dòng tiền, xu hướng theo danh mục, khoản định kỳ và tiến độ mục tiêu. Ở các giai đoạn nâng cao, trợ lý AI có thể giải thích dữ liệu và mô phỏng kịch bản, nhưng không tự ý chuyển tiền, thay đổi ngân sách hoặc quyết định thay người dùng.

---

# 5. Điểm khác biệt

- **Chi tiêu có ngữ cảnh:** Giao dịch không chỉ có số tiền mà còn gắn với ảnh, hoá đơn, món đồ, địa điểm và câu chuyện.
- **Camera là điểm vào nhanh nhất:** Người dùng bắt đầu từ hành động tự nhiên là chụp, thay vì điền một biểu mẫu dài.
- **Quản lý cả sau khi mua:** Ứng dụng tiếp tục hỗ trợ đổi trả, bảo hành, bảo trì và lưu trữ chứng từ sau khi giao dịch kết thúc.
- **Riêng tư theo mặc định:** Dữ liệu tài chính và ảnh chỉ thuộc về người dùng cho đến khi họ chủ động chọn chia sẻ.
- **AI có kiểm soát:** Hệ thống đề xuất và giải thích; người dùng luôn là người xác nhận dữ liệu và hành động quan trọng.
- **Ngôn ngữ không phán xét:** Sản phẩm khuyến khích tiến bộ bền vững, không tạo cảm giác tội lỗi hay biến tiền bạc thành cuộc cạnh tranh.

---

# 6. Một trải nghiệm điển hình

Sau khi mua hàng, người dùng mở camera và chụp hoá đơn. Hệ thống kiểm tra chất lượng ảnh, trích xuất merchant, ngày và tổng tiền, sau đó tìm giao dịch phù hợp nếu dữ liệu thanh toán đã tồn tại. Người dùng xem lại các trường chưa chắc chắn, chọn danh mục rồi xác nhận.

Giao dịch lập tức cập nhật ngân sách. Người dùng có thể chụp thêm món đồ, viết một caption ngắn và lưu vào album riêng tư. Nếu muốn chia sẻ, họ chọn vòng tròn phù hợp và ẩn số tiền hoặc địa điểm trước khi đăng. Khi món đồ gần hết hạn đổi trả hoặc bảo hành, ứng dụng nhắc lại cùng đầy đủ hoá đơn và thông tin cần thiết.

---

# 7. Nguyên tắc thiết kế sản phẩm

- **Nhanh nhưng không đánh đổi độ chính xác:** Tự động hoá những phần chắc chắn, yêu cầu xác nhận khi dữ liệu còn mơ hồ.
- **Một nguồn dữ liệu chuẩn:** Giao dịch, hoá đơn, ngân sách và món đồ liên kết với nhau thay vì tạo các bản ghi mâu thuẫn.
- **Con người giữ quyền quyết định:** Mọi dữ liệu nhạy cảm, đề xuất AI và hành động tài chính quan trọng đều cần người dùng kiểm soát.
- **Riêng tư ngay từ đầu:** Quyền xem, dữ liệu được chia sẻ và thời gian lưu phải luôn rõ ràng.
- **Dễ tiếp cận trong mọi trạng thái:** Luồng chính cần hoạt động tốt với cỡ chữ lớn, trình đọc màn hình, mạng yếu và chế độ ngoại tuyến phù hợp.

---

# 8. Phạm vi phát triển

## MVP

MVP tập trung chứng minh vòng lặp “chụp → hiểu → kiểm soát → nhớ lại” với tài khoản, giao dịch thủ công, camera hoá đơn, OCR thông tin chính, ngân sách tháng, dashboard, album riêng tư, tìm kiếm và xuất dữ liệu.

## Giai đoạn tiếp theo

Các giai đoạn sau mở rộng kết nối tài khoản, OCR dòng hàng, quy tắc tự động, hoá đơn định kỳ, mục tiêu, đổi trả và bảo hành, vòng tròn riêng tư, chi phí chung, báo cáo nâng cao, AI coach có nguồn và trải nghiệm dành cho gia đình hoặc freelancer.

Ứng dụng không được định vị là ngân hàng, dịch vụ cho vay hay công cụ tự động quyết định thay người dùng. Sản phẩm tập trung vào việc ghi nhận, tổ chức, giải thích và hỗ trợ người dùng đưa ra lựa chọn tài chính tốt hơn từ chính dữ liệu của họ.

---

# 9. Tầm nhìn

Ứng dụng hướng tới trở thành nơi người dùng có thể nhìn lại toàn bộ hành trình của một khoản chi: từ lúc thanh toán, xác nhận hoá đơn và cập nhật ngân sách cho đến khi sử dụng, bảo hành, đổi trả hoặc lưu giữ món đồ như một kỷ niệm.

Giá trị của sản phẩm không chỉ nằm ở việc cho biết **đã chi bao nhiêu**, mà còn giúp người dùng hiểu **đã mua gì, vì sao đã mua và khoản chi đó đang phục vụ cuộc sống như thế nào**.
