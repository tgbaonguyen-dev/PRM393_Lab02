# Nhật ký tinh chỉnh Proto-Persona

Ngày: 2026-10-15 · Công cụ: ChatGPT/Codex · Loại hoạt động: desk review và soạn tài liệu, không nghiên cứu người dùng.

## Yêu cầu nguyên văn của người dùng

```text
v làm tầm 3 persona đi, và thêm những phần còn thiếu thì sao? nếu thêm persona thì hãy đối chiếu với dư án đã
```

## Đầu vào thực tế đã đối chiếu

README, ux/persona.md bản cũ, requirements/EXPENSE_TRACKER_REQUIREMENTS.md, requirements/LAB2_REQUIREMENTS.md, ux/user-flow.md, design/screen-spec.md, 10 design decisions, phần handoff liên quan và prompt Stitch ban đầu trong ai-design-log.md. Guideline Persona và Chuẩn chung được đọc trước khi bổ sung; [sổ nguồn R01–R07](../ux/discovery-and-evidence.md) ghi khả năng và giới hạn của từng nguồn.

## Kết quả và lý do

- Giữ Nguyễn Minh là Primary, hoàn thiện 12 trường và ghi rõ tiểu sử gốc chưa được nghiên cứu xác thực.
- Thêm Trần Thảo, Secondary thiên về hiểu cảnh báo/điều chỉnh kế hoạch, liên kết FR-04/05/07.
- Thêm Lê Huy, Secondary thiên về tìm/sửa sai và rà soát báo cáo, liên kết FR-03/05/06.
- Tạo stakeholder/user map, board seed từ tài liệu (không gọi workshop thật), coverage matrix, assumption backlog, scenarios, UI-decision/test matrix, research plan và self-review.
- Không tạo transcript, quote người dùng, E-ID đã thu thập, kết quả test, ảnh workshop hay số liệu nghiên cứu giả. Không chỉnh Figma/prototype hoặc thêm chức năng.

## Quyết định hiện tại

**Modify / cần kiểm chứng:** ba persona dùng được như giả thuyết bao phủ hành vi trong MVP. Không coi số lượng ba là phân khúc đã xác thực; nghiên cứu có thể yêu cầu gộp P01/P03 hoặc thay đổi priority. PDF vẫn có thể là yêu cầu sản phẩm/lab dù A06 về giá trị người dùng chưa được xác minh.

## Tinh gọn sau đối chiếu tiêu chí

Rút gọn mô tả lặp trong ba hồ sơ, giữ đủ 12 trường và chi tiết bắt buộc. Thêm trigger, hệ quả UI, liên kết N/D/T và điều kiện giữ/gộp; nêu rõ ranh giới P01/P03 yếu nhất. Sửa self-review để phân biệt assumptions (#7), phương pháp kiểm tra (#10) với nghiên cứu tương lai. Không tạo câu trả lời/phỏng vấn giả, không điền CSV, không tự chấm ≥80; không sửa deck hoặc prototype trong revision này.

## Ranh giới lịch sử

Đây là revision tài liệu thực hiện sau UI ban đầu. Prompt Stitch cũ vẫn chỉ có Minh và được giữ nguyên; không backdate hai persona mới thành đầu vào thiết kế cũ. Toàn bộ task test được đánh dấu Planned. Các artifact hoàn thành và phần cần dữ liệu thật được phân biệt trong [research-plan-and-review.md](../ux/research-plan-and-review.md).

## Chuẩn bị vòng kiểm chứng theo yêu cầu tiếp theo

Yêu cầu nguyên văn tiếp theo: `v làm v đi`, sau đề xuất phỏng vấn khoảng sáu người, cùng ba task và quyết định giữ/gộp theo evidence.

Đã bổ sung [kế hoạch nghiên cứu và self-review](../ux/research-plan-and-review.md), gồm tiêu chí tuyển, câu hỏi trung tính, ba task dùng chung và quy tắc giữ/gộp persona. Chưa gửi lời mời, chưa có người tham gia, không có transcript/recording/quote hay kết quả nghiên cứu. Không đổi status persona, điểm rubric, slide hoặc prototype vì chưa có dữ liệu để kết luận.
