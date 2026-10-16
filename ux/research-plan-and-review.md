# Research plan và self-review Persona

2026-10-15 · **Chưa triển khai nghiên cứu**. Gói hiện tại là ba Proto-Persona đối chiếu với phạm vi đã có, không phải ba phân khúc đã xác thực.

Kế hoạch dưới đây mô tả cách tuyển người, câu hỏi, ba task dùng chung và quy tắc giữ/gộp persona. Chưa mời hay phỏng vấn ai; kế hoạch sẵn sàng không có nghĩa nghiên cứu đã hoàn thành.

Tham chiếu: [guideline mục 5–8](https://prm393-material.web.app/persona-guideline), [Chuẩn chung C1/C2/C5/C7](https://prm393-material.web.app/#standards). Checklist là tự kiểm; không phải điểm Lab 2 chính thức. Critical chưa đạt vẫn chưa đạt dù tổng cao.

## 1. Câu hỏi nghiên cứu cần trả lời

1. Sinh viên thực sự ghi chi ngay hay theo đợt? Vì sao bỏ ghi?
2. Khi cần quyết định có chi tiếp, họ muốn biết remaining, percent, nguồn chi hay thông tin khác?
3. Có nhóm rà soát sai lệch với mục tiêu/rào cản khác người nhập nhanh không?
4. PDF có ích cho tự rà soát hay chỉ là đầu ra do đề bài yêu cầu?
5. Ba cụm có thật sự khác, hay nên là scenario của cùng một persona?
6. Thiết bị, tăng chữ, mạng và khả năng thao tác nào đang bị bỏ sót?

## 2. Tuyển người tham gia — đề xuất, chưa tuyển

- Target đúng phạm vi: sinh viên 18–24 tuổi tự quản lý chi tiêu cá nhân bằng Android, sống xa gia đình; gồm người đang ghi và người từng bỏ ghi.
- Khởi đầu dự kiến **6 cuộc phỏng vấn/quan sát tổng cộng**, tìm sự đa dạng về cách ghi, kiểm soát ngân sách và rà soát. Đây là kế hoạch trong khoảng gợi ý 6–12 của guideline, không phải 6 người đã tham gia và không đủ để suy rộng thống kê.
- Không tuyển cố định “2 người cho mỗi persona” rồi dùng kết quả đó chứng minh phân nhóm sẵn có. Có thể cần mở rộng/tuyển bổ sung nếu pattern mâu thuẫn hoặc thiếu độ đa dạng.
- Cân nhắc màn hình nhỏ/cũ, người tăng chữ và điều kiện kết nối yếu. Chỉ hỏi thông tin liên quan; không yêu cầu chia sẻ số tài khoản hay số dư thật.
- Giải thích mục đích, tự nguyện tham gia, xin phép ghi âm/ghi hình riêng; không ghi nếu chưa đồng ý. Dùng mã participant, không đưa tên/ảnh nhận diện lên repo public.

## 3. Interview guide — hỏi hành vi đã xảy ra

Gợi ý một phiên 20–30 phút, có thể thay đổi theo người tham gia; thời lượng là kế hoạch.

- Lần gần nhất bạn trả một khoản nhỏ là lúc nào? Sau đó bạn làm gì để nhớ khoản đó?
- Bạn có thể kể lại lần gần nhất bắt đầu ghi chi rồi bỏ không? Điều gì xảy ra?
- Lần gần nhất bạn cần biết còn có thể chi bao nhiêu, bạn đã xem/tính bằng cách nào?
- Có lần nào cảnh báo ngân sách khiến bạn đổi quyết định không? Nếu không, vì sao?
- Lần gần nhất số tổng không khớp điều bạn nhớ, bạn đã tìm nguyên nhân thế nào?
- Bạn đã từng sửa/xóa nhầm chưa? Bạn xử lý ra sao?
- Lần gần nhất bạn dùng một báo cáo chi tiêu là khi nào? Dùng để làm gì? Không giả định ai cũng cần PDF.
- Thiết bị, chữ, kết nối hay thao tác nào làm công việc khó hơn?

Không hỏi dẫn kiểu “Bạn có thích nút Undo của app chúng tôi không?”. Cho người tham gia mô tả quy trình hiện tại trước khi giới thiệu prototype. Không dùng persona minh họa làm đáp án đúng khi phỏng vấn.

## 4. Tổng hợp và cập nhật sau nghiên cứu

1. Tạo record E-ID thật, gắn participant mã hóa, ngày, bối cảnh, consent và vị trí đoạn liên quan; lưu raw evidence ở nơi hạn chế quyền, không public PII.
2. Phân loại **Observed / Reported / Inferred / Assumed**. Trích dẫn chỉ dùng khi có record gốc được phép; câu do AI viết không trở thành quote thật.
3. Chuyển note vào affinity board kèm E-ID; ghi cả phản ví dụ, không ép dữ liệu vào ba nhóm đã chọn.
4. So sánh goals/behaviors/context/constraints. Gộp P01/P03 nếu chỉ khác thời điểm dùng; tách nhóm mới chỉ khi tạo khác biệt thiết kế có ý nghĩa.
5. Cập nhật 12 trường, priority, coverage, backlog và matrix. Nếu evidence chưa đủ, giữ nhãn Proto-Persona.
6. Chạy [T01–T08](scenarios-and-tests.md#kế-hoạch-test), tách rõ usability insight và functional defect; ghi cả failed/blocked.

## 5. Mẫu record bằng chứng trống

Đây là schema, **không phải các record đã thu thập**:

```text
Evidence ID: cấp sau khi có dữ liệu thật
Date / artifact version:
Participant ID (ẩn danh) / consent scope:
Task and context:
Evidence type: Observed | Reported
Raw source and timestamp/line reference:
Observation or exact permitted quote:
Interpretation (Inferred), reason and counterexample:
Related assumption / persona / need / test:
Uncertainty / next check:
Privacy and access restriction:
```

Inferred và Assumed nằm ở tầng diễn giải, không dùng thay raw source. Hiện không có participant record, transcript, interview finding hay ảnh workshop để nộp như đã thực hiện.

## 6. Self-review theo 10 mục của guideline

Trạng thái dưới đây chỉ đánh giá **artifact hiện có**, chưa tự quy đổi thành 80/100 hay điểm giảng viên. Với rubric mỗi mục 10 điểm, mục “partial” không được tự tính đủ điểm.

| # | Tiêu chí | Hiện trạng | Cần làm tiếp |
| --- | --- | --- | --- |
| 1 | Phạm vi, tasks, target user | Có: R01/R02 và mục 1 persona | Xác minh vấn đề với người dùng |
| 2 | User/Stakeholder Map và nhóm bị bỏ sót | Có bản đề xuất từ desk review | Review với nhóm, bổ sung từ nghiên cứu |
| 3 | Số lượng phù hợp phạm vi | Có lý do đề xuất 1 Primary + 2 Secondary | Chưa có dữ liệu chứng minh ba cụm; kiểm A08 |
| 4 | Phân biệt bằng goals/behaviors/context/constraints | Đã mô tả khác biệt giả định, không chỉ đổi tên/tuổi | Cần pattern thực tế trước khi gọi khác biệt đã xác thực |
| 5 | Đủ 12 trường, ngắn và dùng được | Cả ba có 12 trường và chi tiết bắt buộc Lab 2 | Review cách diễn đạt; bản slide chỉ tóm tắt, không thay hồ sơ |
| 6 | Needs là kết quả, không giả làm tính năng | Goals/JTBD/Nxx tách khỏi UI solution | Kiểm tra ngôn ngữ bằng hành vi người dùng |
| 7 | Có evidence hoặc ghi rõ assumptions | Đã dùng nhánh assumptions minh bạch: Proto/Assumed; R ≠ E | Không bắt buộc dựng phỏng vấn để đáp ứng nhánh này; chỉ đổi trạng thái khi có dữ liệu thật |
| 8 | Affinity Board/pattern giải thích phân khúc | Chỉ có board seed từ tài liệu, **chưa có board nghiên cứu/workshop** | Thu note có nguồn và clustering thật; không tính seed thành nghiên cứu đã làm |
| 9 | Primary có scenario và success criteria | SC01, T01/T02; Secondary cũng có SC02/SC03 | Chạy test, không nhầm target với result |
| 10 | UI decision/hypothesis và cách test liên kết persona | Có matrix Persona → Nxx → quyết định hiện có → Txx, task và tiêu chí | Artifact về phương pháp đã có; chạy test là bước kiểm chứng tiếp theo, không phải kết quả đã có |

**Cách đọc rubric:** mục 7 cho phép assumptions minh bạch; mục 10 yêu cầu quyết định/giả thuyết liên kết với cách kiểm tra. Không tự thêm điều kiện rằng hai mục này chỉ đạt khi đã phỏng vấn hoặc test xong. Mục 9 cũng phân biệt success criteria đề xuất với kết quả đo. Các hoạt động nghiên cứu ở cột cuối là hướng củng cố, không mặc nhiên là điều kiện chấm từng mục.

**Kết luận tự kiểm:** cấu trúc và phương pháp đã có; điểm yếu còn lại là mức thuyết phục của khác biệt hành vi (#4) và cơ sở tổng hợp phân nhóm (#8). Board hiện tại tổng hợp tài liệu có nhãn giả định, không phải affinity từ người dùng. Mức độ chấp nhận phụ thuộc giảng viên; không bảo đảm ≥80 hay bypass Critical bằng cách thêm tên persona.

## 7. Deliverable checklist và ranh giới hoàn thành

- [x] Problem statement và phạm vi, đối chiếu dự án hiện có.
- [x] User/Stakeholder Map bản desk review.
- [x] Ba Proto-Persona đủ 12 trường, primary/secondary và giả định rõ.
- [x] Coverage Matrix và các scenario.
- [x] Assumption/Research Backlog, Persona → Need → UI → Test.
- [x] Research plan, schema evidence và self-review minh bạch.
- [ ] Workshop thực tế, ảnh brainstorming/affinity có consent và provenance.
- [ ] Tuyển người, nghiên cứu, note/transcript ẩn danh có nguồn.
- [ ] Affinity có pattern nghiên cứu và persona cập nhật theo evidence.
- [ ] Usability test thật, kết quả và revision sau test.
- [ ] Frame-level accessibility/responsive và mọi nhánh prototype được kiểm đầy đủ.

Các mục còn trống cần hoạt động thật hoặc quyền source, không thể hoàn thành trung thực chỉ bằng cách soạn tài liệu. Không đưa cuộc nghiên cứu dự kiến vào lịch sử thiết kế đã diễn ra.
