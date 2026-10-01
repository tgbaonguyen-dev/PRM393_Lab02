# Screen Specifications (Đặc tả màn hình)

## Quản lý chi tiêu, lưu giữ khoảnh khắc mua sắm (Chụp → Hiểu → Kiểm soát → Nhớ lại)

Tài liệu này đặc tả mục đích thiết kế, nội dung hiển thị và mối liên kết với User Flow cho toàn bộ **8 màn hình chính** của ứng dụng di động (chuẩn kích thước hiển thị: **360 × 800 dp**).

---

## 1. SCR_01: Home Dashboard (Tổng quan tài chính & Khoảnh khắc)

- **Mục đích thiết kế:** Là màn hình chính (Top-level) khi người dùng mở app. Giúp người dùng nắm bắt tức thì tình hình số dư các nguồn tiền, tiến độ tiêu dùng trong tháng và xem lại các khoảnh khắc chi tiêu vừa thực hiện mà không cảm thấy áp lực.
- **Nội dung hiển thị:**
  - **Top Bar:** Lời chào cá nhân hóa theo buổi ("Chào Tuấn!"), avatar người dùng và nút chuông thông báo (nhắc nợ/hạn mức).
  - **Card Tổng tài sản (Total Balance Card):** Tổng số dư gộp và chi tiết phân bổ nhanh (Tiền mặt, Tài khoản Ngân hàng, Ví điện tử).
  - **Thanh tiến độ ngân sách tháng (Monthly Budget Progress):** Thể hiện % đã chi tiêu trên tổng ngân sách, số ngày còn lại trong tháng và trạng thái tốc độ chi (bình thường / báo động).
  - **Quick Actions Row:** Phím tắt "Thêm tay (+)", "Xem báo cáo", "Chuyển tiền".
  - **Recent Transactions & Moments Feed:** Danh sách cuộn dọc các giao dịch gần đây; mỗi giao dịch có thumbnail ảnh món đồ/hóa đơn, merchant, số tiền (âm/dương), danh mục và tag câu chuyện/khoảnh khắc.
  - **Bottom Navigation Bar:** 4 tabs (Home, Sổ giao dịch, Ngân sách, Bộ sưu tập món đồ) cùng **Floating Camera Button nổi bật ở chính giữa**.
- **Thuộc Flow nào:**
  - **Flow 1:** Điểm bắt đầu (chạm nút Camera) và điểm trở về sau khi lưu.
  - **Flow 2:** Điểm bắt đầu (bấm nút '+' thêm thủ công) và cập nhật số dư sau khi lưu.
  - **Flow 3:** Điểm điều hướng về trang chủ.

---

## 2. SCR_02: Add Transaction Manual (Ghi nhận chi tiêu thủ công)

- **Mục đích thiết kế:** Dành cho các khoản chi tiền mặt nhỏ lẻ không có hóa đơn (ví dụ: gửi xe, trà đá, ăn trưa vỉa hè). Tối ưu hóa tốc độ nhập liệu để hoàn tất trong dưới 15 giây chỉ bằng 1 tay.
- **Nội dung hiển thị:**
  - **Top Bar:** Nút đóng 'X' (hủy thao tác) và tiêu đề "Ghi nhận chi tiêu".
  - **Trường hiển thị số tiền lớn (Amount Display):** Hiển thị số tiền to rõ ràng (ví dụ: `50.000 đ`), hỗ trợ xóa lùi (Backspace).
  - **Bàn phím số tích hợp (Custom In-app Numpad):** Các phím số từ 0–9 to bản (touch target $\ge 48 \times 48\text{ dp}$), phím "000" để gõ nhanh mệnh giá tiền Việt Nam, phím xóa.
  - **Selector Danh mục chi tiêu:** Grid icon gồm 8 danh mục phổ biến (Ăn uống, Đi lại, Nhà trọ, Mua sắm, Học tập, Giải trí, Y tế, Khác).
  - **Selector Nguồn tiền (Source of Funds):** Chips chọn nguồn trừ tiền (Tiền mặt, Thẻ ngân hàng, Ví Momo).
  - **Input Ghi chú & Ngày:** Ô nhập text ngắn mô tả nhanh ("Bún bò sáng") và Date Picker (mặc định hôm nay).
  - **Nút hành động chính (Primary CTA):** Nút "Lưu giao dịch" (Full-width, màu Primary).
- **Thuộc Flow nào:**
  - **Flow 2 (Trọng tâm):** Thực hiện luồng nhập tay, kiểm tra tính hợp lệ của số tiền và kích hoạt overlay cảnh báo nếu vượt hạn mức ngân sách tháng.

---

## 3. SCR_03: Scan Receipt & Item Camera (Camera chụp hoá đơn & Món đồ)

- **Mục đích thiết kế:** Điểm vào nhanh nhất của ứng dụng theo triết lý "Camera First". Tự động bắt khung hóa đơn hoặc chụp nhanh món đồ vừa mua ngay tại quầy thanh toán.
- **Nội dung hiển thị:**
  - **Viewfinder Fullscreen:** Giao diện camera tràn màn hình với khung hướng dẫn canh biên hóa đơn (Document Edge Detection box màu trắng/xanh).
  - **Top Controls:** Nút tắt camera (X), nút bật/tắt đèn Flash, nút chuyển đổi chế độ chụp: [Chụp Hóa đơn (Receipt)] / [Chụp Món đồ (Item)].
  - **Bottom Shutter Bar:**
    - Nút mở Thư viện ảnh (Gallery Picker) bên trái để tải ảnh hóa đơn có sẵn.
    - Nút chụp tròn lớn ở chính giữa (Shutter Button).
    - Hướng dẫn trực quan: "Giữ hóa đơn phẳng và đủ sáng".
- **Thuộc Flow nào:**
  - **Flow 1 (Trọng tâm):** Bắt đầu hành trình "Chụp $\rightarrow$ Hiểu $\rightarrow$ Kiểm soát $\rightarrow$ Nhớ lại".

---

## 4. SCR_04: OCR Review & Story Attachment (Xác nhận OCR & Đính kèm khoảnh khắc)

- **Mục đích thiết kế:** Vừa cho phép kiểm tra, chỉnh sửa dữ liệu do AI/ML Kit trích xuất (tính minh bạch, người dùng nắm quyền kiểm soát), vừa cho phép làm giàu dữ liệu bằng ảnh món đồ và cảm xúc mua sắm.
- **Nội dung hiển thị:**
  - **Top Bar:** Nút Back mũi tên và tiêu đề "Xác nhận giao dịch".
  - **Thumbnail Hóa đơn gốc:** Ảnh thu nhỏ của hóa đơn vừa chụp, bấm vào để phóng to đối soát.
  - **Banner Cảnh báo độ tin cậy (Confidence Alert):**
    - Nếu Confidence $\ge 80\%$: Hiện nhãn xanh "Đã trích xuất tự động thành công".
    - Nếu ảnh mờ/Confidence thấp: Hiện Banner vàng có icon cảnh báo "Ảnh hơi mờ, vui lòng kiểm tra lại Tổng tiền".
  - **Các trường dữ liệu trích xuất (Editable Fields):**
    - Ô Tổng tiền (Amount) - trường quan trọng nhất, cho phép chạm vào sửa tay nếu nhận diện lệch.
    - Tên cửa hàng/Merchant (ví dụ: "Circle K Đội Cấn").
    - Ngày & giờ giao dịch.
    - Gợi ý danh mục tự động.
  - **Khu vực "Khoảnh khắc mua sắm" (Story & Item Attachment):**
    - Nút đính kèm thêm ảnh chụp món đồ thực tế (Item Photo).
    - Ô viết cảm nghĩ ngắn (Caption/Story - ví dụ: "Tự thưởng sau khi nộp đồ án").
    - Toggle quyền riêng tư: [Chỉ mình tôi] / [Chia sẻ với Người yêu/Gia đình].
  - **Nút hành động chính:** Nút "Lưu khoảnh khắc & Giao dịch".
- **Thuộc Flow nào:**
  - **Flow 1 (Trọng tâm):** Nhánh chính hoàn tất lưu OCR và nhánh phục hồi khi ảnh mờ (sửa tiền bằng tay hoặc chụp lại).

---

## 5. SCR_05: Transaction History & Search (Sổ giao dịch & Tra cứu)

- **Mục đích thiết kế:** Cung cấp danh sách chi tiết các khoản thu/chi theo dòng thời gian, giúp người dùng tra cứu lại chứng từ, merchant hoặc tìm kiếm hóa đơn khi cần đối soát.
- **Nội dung hiển thị:**
  - **Header Search Bar:** Thanh tìm kiếm đa năng (gõ tên món đồ, tên quán, danh mục).
  - **Filter Chips:** Các nút lọc nhanh: [Tất cả], [Có hóa đơn 🧾], [Có ảnh món đồ 📸], [Tuần này], [Tháng này].
  - **Thống kê nhanh kỳ này:** Banner nhỏ hiển thị tổng thu, tổng chi và số dư ròng trong khoảng thời gian đang lọc.
  - **Danh sách giao dịch theo nhóm ngày (Sticky Date Grouping):**
    - Tiêu đề ngày (ví dụ: "Hôm nay, 30 Th09 - Chi: 125.000 đ").
    - Các thẻ giao dịch: Icon danh mục, tên merchant/món đồ, nguồn tiền trừ, số tiền màu đỏ (-) hoặc xanh lá (+), badge icon camera nếu có đính kèm hóa đơn/món đồ.
  - **Trạng thái rỗng (Empty State):** Minh họa thân thiện khi không tìm thấy kết quả tìm kiếm kèm nút "Đặt lại bộ lọc".
- **Thuộc Flow nào:**
  - **Flow 1 & Flow 2:** Xem lại giao dịch vừa được tạo.
  - **Flow 3 (Trọng tâm):** Thực hiện tìm kiếm, lọc hóa đơn và chuyển sang xem chi tiết món đồ.

---

## 6. SCR_06: Budget & Expense Control (Ngân sách & Kiểm soát chi tiêu)

- **Mục đích thiết kế:** Giúp người dùng theo dõi hạn mức chi tiêu từng danh mục theo triết lý "không phán xét", cảnh báo sớm nguy cơ thâm hụt tài chính cuối tháng và đề xuất điều chỉnh linh hoạt.
- **Nội dung hiển thị:**
  - **Bộ chọn tháng:** Ví dụ "Tháng 10/2026" kèm mũi tên chuyển tháng.
  - **Thẻ Tổng quan ngân sách (Overall Budget Card):**
    - Tổng hạn mức tháng (ví dụ: `4.000.000 đ`).
    - Số tiền đã tiêu và số tiền còn lại an toàn để chi mỗi ngày (`Còn 45.000 đ/ngày`).
    - Thanh Linear Progress Bar trực quan (Xanh: an toàn < 70%, Vàng: cảnh báo 70-90%, Đỏ: vượt trần > 100%).
  - **Danh sách ngân sách theo từng danh mục (Category Budget List):**
    - Thẻ từng mục: Ăn uống, Tiền nhà/phòng trọ, Đi lại xe cộ, Mua sắm, Giải trí.
    - Mỗi thẻ gồm: Tên mục, icon, số tiền đã chi / hạn mức đặt ra, thanh progress bar riêng.
  - **Nút điều chỉnh hạn mức:** Cho phép tạo mới ngân sách hoặc sửa hạn mức khi có nhu cầu ngoại lệ.
- **Thuộc Flow nào:**
  - **Flow 2:** Cung cấp ngưỡng kiểm tra tự động khi nhập chi tiêu và hiển thị trạng thái chuyển đỏ nếu vượt hạn mức.
  - **Flow 3:** Cập nhật lại số liệu sau khi tra cứu chi tiêu.

---

## 7. SCR_07: Shopping Moments & Item Collection (Nhật ký mua sắm & Bộ sưu tập món đồ)

- **Mục đích thiết kế:** Hiện thực hóa giá trị "Nhớ lại" (Recall). Biến các khoản chi thành album kỷ niệm những món đồ đã sở hữu, đồng thời đóng vai trò là "két sắt lưu trữ" bảo hành và hạn đổi trả.
- **Nội dung hiển thị:**
  - **Top Bar:** Tiêu đề "Bộ sưu tập món đồ" và nút chuyển đổi giao diện [Dạng Lưới (Grid)] / [Dạng Dòng thời gian (Timeline)].
  - **Lưới ảnh món đồ (Masonry / Grid View):**
    - Các thẻ món đồ có ảnh chụp thực tế chất lượng cao.
    - Badge trạng thái bảo hành: "Bảo hành còn 6 tháng" (xanh), "Hết hạn đổi trả" (xám).
    - Tên món đồ, ngày mua và giá tiền.
  - **Modal Chi tiết món đồ (Khi chạm vào một thẻ):**
    - Slide ảnh món đồ + ảnh hóa đơn gốc.
    - Thông tin cửa hàng, số seri sản phẩm, thời hạn bảo hành.
    - Nút "Xem hóa đơn gốc phóng to" để mang đi bảo hành.
    - Nút "Chia sẻ khoảnh khắc" sang mạng xã hội hoặc nhóm gia đình.
- **Thuộc Flow nào:**
  - **Flow 1:** Nơi tiếp nhận và hiển thị món đồ mới sau khi quét hóa đơn và chụp ảnh kỷ niệm.
  - **Flow 3 (Trọng tâm):** Điểm đến để xem chi tiết hóa đơn gốc, kiểm tra hạn bảo hành và kỷ niệm mua sắm.

---

## 8. SCR_08: User Settings & Financial Profile (Cài đặt tài khoản & Ví tiền)

- **Mục đích thiết kế:** Quản lý các nguồn tiền cá nhân, thiết lập ngưỡng cảnh báo tài chính thông minh và quản lý vòng tròn riêng tư.
- **Nội dung hiển thị:**
  - **Hồ sơ người dùng:** Avatar, tên "Trần Quốc Tuấn", email sinh viên.
  - **Quản lý nguồn tiền (Wallets & Accounts):** Danh sách liên kết: Ví Tiền mặt, Thẻ Vietcombank, Ví Momo, nút "Thêm ví mới".
  - **Cài đặt cảnh báo thông minh (Smart Alert Preferences):**
    - Toggle nhận thông báo cảnh báo khi chi tiêu ngày vượt ngưỡng (ví dụ: cảnh báo khi tiêu > 150k/ngày).
    - Cài đặt ngày nhắc nhở tổng kết tuần/tháng.
  - **Cài đặt vòng tròn riêng tư (Privacy Circles):** Quản lý ai được xem các khoảnh khắc mua sắm chung (Cá nhân, Người yêu, Gia đình).
  - **Cài đặt tiếp cận (Accessibility):** Tùy chọn cỡ chữ lớn, giao diện tương phản cao.
- **Thuộc Flow nào:**
  - Hỗ trợ dữ liệu nền tảng cho **Flow 1, Flow 2** (chọn nguồn tiền) và **Flow 3** (quyền xem hóa đơn).
