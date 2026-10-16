# Persona và vấn đề người dùng

Phiên bản 2026-10-15 · 1 Primary + 2 Secondary · **cả ba là Proto-Persona, chưa được nghiên cứu xác thực**.

Tên, tuổi và tiểu sử là minh họa. Mọi phát biểu về thói quen, khó khăn và động lực người dùng đều là giả định cần kiểm chứng; tài liệu dự án chỉ chứng minh phạm vi thiết kế, không phải bằng chứng phỏng vấn. Không có số người tham gia, transcript hay kết quả usability test được tạo ra trong lần bổ sung này.

## 1. Phạm vi và cách chọn

Sản phẩm hiện có: sinh viên 18–24 tuổi tự quản lý chi tiêu cá nhân trên Android; ba flow và 12 screen IDs được giữ nguyên. Không bổ sung OCR, bank sync, quản lý tiền nhóm, tài khoản phụ huynh, AI coach hoặc tính năng quản lý thu nhập.

| ID | Priority | Archetype giả định | Khác biệt cần thiết kế | Ánh xạ hiện có |
| --- | --- | --- | --- | --- |
| P01 · Nguyễn Minh | Primary | Ghi ngay trong phiên ngắn | Giảm gián đoạn và công nhập liệu ngay khi thanh toán | Flow 1; HM-01, TX-02, TX-03 |
| P02 · Trần Thảo | Secondary | Chủ động kiểm soát hạn mức | Hiểu sớm danh mục cần chú ý và điều chỉnh có căn cứ | Flow 3; HM-01, BD-01/02/03, NT-01, IN-01 |
| P03 · Lê Huy | Secondary | Rà soát định kỳ để tin số liệu | Tìm lại nguồn giao dịch, sửa sai và tổng hợp cuối kỳ | Flow 2 + phần báo cáo Flow 3; TX-01/02/03, IN-01, EX-01 |

Minh là Primary do vòng lặp giá trị và prompt Stitch ban đầu ưu tiên ghi chi nhanh; đây là quyết định phạm vi, không phải kết luận nhóm này phổ biến nhất trong dân số. Thảo và Huy là giả thuyết về nhu cầu khác biệt, không phải hai role mới. Một người thật có thể chuyển giữa cả ba kiểu hành vi; nghiên cứu có thể dẫn tới gộp lại. Không suy luận “ba flow nên phải có ba persona”.

## 2. P01 — Nguyễn Minh · Primary

| Trường lõi | Nội dung |
| --- | --- |
| 01. Identity & Archetype | Nguyễn Minh, 21 tuổi, sinh viên năm ba, thực tập bán thời gian; **người ghi chi ngay trong phiên ngắn**. |
| 02. Persona Priority | **Primary**: giảm công ghi để người dùng không bỏ khoản chi hằng ngày. |
| 03. Usage Context | Sống xa gia đình tại TP.HCM; sau khi ăn, gửi xe hoặc mua tài liệu; Android tầm trung, có thể dùng một tay khi đang di chuyển và bị phân tán chú ý. |
| 04. Goals | (1) Ghi đúng khoản vừa trả trước khi quên; (2) hiểu ngay ảnh hưởng tới ngân sách còn lại; (3) tiếp tục việc đang làm mà không bị form kéo dài. |
| 05. Job to Be Done | Khi vừa thanh toán, tôi muốn ghi nhanh và hiểu ảnh hưởng tới ngân sách để không phải nhớ hoặc ghi bù. Câu nhóm soạn, không phải trích dẫn. |
| 06. Current Behaviors | Giả định: từng dùng ghi chú rồi bỏ; mở app dưới một phút; không quen bảng tính. |
| 07. Pain Points | Nhiều khoản nhỏ dễ bị quên; form nhiều bước làm trì hoãn ghi; nhập lại sau lỗi mạng làm mất công và tăng nguy cơ ghi sai. |
| 08. Motivations | Nhanh, ít công nhớ, thấy ngay số còn lại và tránh cảm giác bị phán xét. |
| 09. Constraints | Giả định nhận 5.000.000 VND/tháng và thu nhập thực tập không cố định; đây là bối cảnh, không yêu cầu thêm module thu nhập. Phiên ngắn, mạng có thể yếu. Accessibility cần kiểm: body ≥14sp, hit area ≥48×48dp, text scaling, số tiền rõ ngoài trời, không dựa riêng vào màu. Google sign-in là phương án thiết kế; sở thích thực tế chưa xác minh. |
| 10. Key Scenarios | [SC01](scenarios-and-tests.md#sc01--ghi-khoản-chi-ngay-sau-thanh-toán): vừa trả tiền → ghi số tiền/danh mục/ngày → lưu → xem detail và Home cập nhật; nhánh nhập sai hoặc lỗi mạng không làm mất dữ liệu. |
| 11. Success Criteria | Mục tiêu kế thừa PRD: hoàn thành ghi chi và thấy ngân sách cập nhật **<20 giây**, không cần hướng dẫn; transaction chỉ xuất hiện một lần và tổng tiền đúng. [T01, T02](scenarios-and-tests.md#kế-hoạch-test) **chưa chạy với người dùng**. |
| 12. Evidence & Status | **Proto-Persona / Assumed**. Cơ sở phạm vi: R01–R04 trong [sổ nguồn](discovery-and-evidence.md#1-sổ-nguồn-và-ranh-giới-bằng-chứng). Giả định hành vi: A01–A02, A07–A08. Chưa có E-ID phỏng vấn/quan sát. |

## 3. P02 — Trần Thảo · Secondary

| Trường lõi | Nội dung |
| --- | --- |
| 01. Identity & Archetype | Trần Thảo, 20 tuổi, sinh viên năm hai sống xa nhà; **người chủ động kiểm soát hạn mức**. Tên và tuổi minh họa, không quyết định phân khúc. |
| 02. Persona Priority | **Secondary**: bổ sung góc nhìn ra quyết định ngân sách, không tạo bộ màn hình riêng. |
| 03. Usage Context | Giả định kiểm tra ngân sách trước một khoản chi hoặc khi nhận cảnh báo; dùng Android và thường xem nhanh trong ngày, không muốn đọc báo cáo dài. |
| 04. Goals | (1) Nhận ra danh mục đang có nguy cơ vượt hạn mức; (2) hiểu các khoản chi gây ra tình trạng đó; (3) lựa chọn giảm chi hoặc điều chỉnh hạn mức có chủ đích. |
| 05. Job to Be Done | Khi danh mục sắp hết ngân sách, tôi muốn hiểu số còn lại và nguyên nhân để quyết định khoản chi tiếp theo. Câu nhóm soạn, không phải trích dẫn. |
| 06. Current Behaviors | Giả định: chia tiền theo nhu cầu, nhẩm số còn lại, đối chiếu ghi chú/lịch sử thanh toán. |
| 07. Pain Points | Chỉ thấy tổng chi mà không biết danh mục nào cần chú ý; phần trăm thiếu số tiền còn lại khó diễn giải; cảnh báo đỏ/phán xét không giải thích nguyên nhân khiến người dùng bỏ qua. |
| 08. Motivations | Chủ động, ổn định kế hoạch, hiểu lý do trước khi thay đổi giới hạn; không bị ép “tăng hạn mức” như cách mặc định xử lý vượt chi. |
| 09. Constraints | Ngân sách sinh hoạt hữu hạn, chú ý ngắn, màn hình nhỏ; không giả định tăng hạn mức sẽ tạo thêm tiền. Accessibility cần kiểm: trạng thái có icon + text + màu, contrast, body ≥14sp, vùng chạm ≥48×48dp và nội dung không cắt khi tăng chữ. |
| 10. Key Scenarios | [SC02](scenarios-and-tests.md#sc02--hiểu-cảnh-báo-và-điều-chỉnh-có-căn-cứ): Home/notification hoặc BD-01 → BD-02 → xem nguồn chi → chọn giữ hoặc sửa hạn mức ở BD-03 → xem số cập nhật. |
| 11. Success Criteria | Mục tiêu kế thừa PRD: chỉ ra danh mục cần chú ý **<10 giây từ Home**; giải thích được trạng thái bằng số còn lại và một nguồn giao dịch; nếu sửa hạn mức, remaining/percent phải cập nhật đúng. [T03, T04](scenarios-and-tests.md#kế-hoạch-test) chưa chạy. |
| 12. Evidence & Status | **Proto-Persona / Assumed**. R01, R02, R04–R05 chứng minh chức năng đã có trong đặc tả, không chứng minh Thảo có thật. A03–A04, A07–A08 cần kiểm chứng. Chưa có E-ID nghiên cứu. |

## 4. P03 — Lê Huy · Secondary

| Trường lõi | Nội dung |
| --- | --- |
| 01. Identity & Archetype | Lê Huy, 22 tuổi, sinh viên năm cuối có việc làm thêm; **người rà soát định kỳ để tin số liệu**. Thông tin cá nhân chỉ minh họa. |
| 02. Persona Priority | **Secondary**: ưu tiên truy vết và độ đúng; có thể gộp P01 nếu không có khác biệt thực chất. |
| 03. Usage Context | Giả định: rà lại trên Android cuối tuần/tháng, tập trung hơn lúc thanh toán. |
| 04. Goals | (1) Tìm đúng khoản cần đối chiếu và sửa sai; (2) xóa hoặc khôi phục mà không mất kiểm soát dữ liệu; (3) hiểu tổng chi cuối kỳ và mở bản tổng hợp tháng. |
| 05. Job to Be Done | Khi tổng không khớp điều tôi nhớ, tôi muốn truy ra và sửa giao dịch để tin kết quả. Câu nhóm soạn, không phải trích dẫn. |
| 06. Current Behaviors | Giả định: kiểm tra theo đợt, đối chiếu thủ công với ghi chú/lịch sử thanh toán; không bank sync; nhu cầu PDF chưa xác thực. |
| 07. Pain Points | Khó tìm khoản cũ trong danh sách dài; không biết sửa/xóa có làm tổng thay đổi đúng không; xóa nhầm và báo cáo sai kỳ làm giảm niềm tin. |
| 08. Motivations | Chính xác, kiểm soát, giải thích được số tổng và giảm công rà soát lại; ưu tiên tin dữ liệu hơn tốc độ nhập từng khoản. |
| 09. Constraints | Chỉ quản lý tài chính cá nhân, không quản lý tiền nhóm hay kế toán. App hiện là prototype dữ liệu mẫu; sửa/tìm kiếm thật và PDF thật cần test ở hệ thống có dữ liệu. Accessibility cần kiểm: dòng có ngày/danh mục/số tiền dễ đọc, action xóa rõ, Undo thao tác được, body ≥14sp, hit area ≥48×48dp, text scaling. |
| 10. Key Scenarios | [SC03](scenarios-and-tests.md#sc03--rà-soát-sửa-sai-và-mở-báo-cáo): TX-01 → đúng TX-03 → sửa tại TX-02 hoặc xóa/Undo → kiểm tra dữ liệu → IN-01/EX-01 chọn đúng kỳ và mở PDF preview. |
| 11. Success Criteria | Chọn đúng giao dịch theo đề bài; sửa đúng trường; tổng và ngân sách khớp dữ liệu chuẩn; Cancel không xóa, Undo khôi phục một lần; nhận biết đúng tháng/trạng thái báo cáo và mở được preview. [T05–T07](scenarios-and-tests.md#kế-hoạch-test) chưa chạy; không tự thêm ngưỡng thời gian chưa có căn cứ. |
| 12. Evidence & Status | **Proto-Persona / Assumed**. R01–R02, R04–R05 xác nhận phạm vi transaction/Insights/PDF trong repo; A05–A08 chưa xác thực. Chưa có E-ID người dùng; functional rehearsal không phải nghiên cứu persona. |

## 5. Problem statement chung

Sinh viên sống xa nhà cần ghi đúng và hiểu được ảnh hưởng của khoản chi lên ngân sách cá nhân, vì nhiều khoản nhỏ, cảnh báo thiếu ngữ cảnh và khó truy lại sai lệch có thể làm họ mất kiểm soát trước cuối tháng. Đây là giả thuyết vấn đề kế thừa và mở rộng cách diễn đạt của dự án, chưa phải kết luận khảo sát.

## 6. Hồ sơ đi kèm và trạng thái

- [User/Stakeholder Map, board tổng hợp từ tài liệu, coverage matrix và assumption backlog](discovery-and-evidence.md).
- [Scenarios, ma trận Persona → Need → UI decision → Test và kế hoạch test](scenarios-and-tests.md).
- [Kế hoạch nghiên cứu, mẫu ghi bằng chứng và tự đánh giá theo guideline](research-plan-and-review.md).
- [Kế hoạch nghiên cứu và quy tắc giữ/gộp](research-plan-and-review.md): phỏng vấn trung tính và cùng ba task cho mọi người; hiện chưa triển khai với người tham gia thật.

Đây là phần bổ sung tài liệu ở thời điểm hiện tại, **không sửa lại lịch sử rằng UI ban đầu đã được nghiên cứu với ba persona**. Prompt Stitch gốc dùng Minh và được giữ nguyên. Hai Secondary mới sẽ được dùng cho các vòng review/test tiếp theo. Chưa thay đổi Figma, màn hình, flow hoặc tính năng.

