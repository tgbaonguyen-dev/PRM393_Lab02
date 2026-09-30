# Information Architecture & User Flows — Dự án PicKet

## Quản lý chi tiêu, lưu giữ khoảnh khắc mua sắm (Chụp → Hiểu → Kiểm soát → Nhớ lại)

---

## 1. Information Architecture (Kiến trúc thông tin & Cấu trúc điều hướng)

Ứng dụng được thiết kế theo tư duy Mobile-First với **Bottom Navigation Bar gồm 4 Tab chính** cùng **Nút hành động trung tâm (Camera Quick-Action)** để tối ưu hóa vòng lặp cốt lõi _"Chụp để ghi nhận"_:

```text
App Root (Main Application)
├── [Tab 1] Home Dashboard (SCR_01) ── Top-level
│     ├── (+) Add Transaction Manual (SCR_02) ── Modal Screen / Sheet
│     │     └── [Dialog] Budget Exceeded Warning (Overlay Dialog)
│     └── [Center Action] Scan Receipt & Item Camera (SCR_03) ── Fullscreen Modal
│           └── OCR Review & Story Attachment (SCR_04) ── Sub-screen
│                 └── [Dialog] Low Confidence Warning (Inline Alert / Dialog)
├── [Tab 2] Transaction History & Search (SCR_05) ── Top-level
│     └── Filter & Search Bottom Sheet (Lọc theo danh mục, thời gian, merchant)
├── [Tab 3] Budget & Expense Control (SCR_06) ── Top-level
│     └── Edit Category Budget Modal (Điều chỉnh hạn mức danh mục)
├── [Tab 4] Shopping Moments & Item Collection (SCR_07) ── Top-level (Nhật ký mua sắm)
│     └── Item Detail Modal (Xem ảnh món đồ, hoá đơn đính kèm, bảo hành, ghi chú)
└── [Header Action] User Settings & Financial Profile (SCR_08) ── Push Screen
```

### Danh sách 8 màn hình chính (Chuẩn kích thước 360 × 800 dp):

1. **SCR_01 - Home Dashboard (Tổng quan tài chính & Khoảnh khắc):** Số dư các nguồn tiền, tiến độ ngân sách tháng, cảnh báo tốc độ chi tiêu, danh sách giao dịch & khoảnh khắc gần đây.
2. **SCR_02 - Add Transaction Manual (Ghi nhận chi tiêu thủ công):** Bàn phím số lớn (Numpad), chọn danh mục, nguồn tiền (tiền mặt/ngân hàng/ví), ghi chú nhanh.
3. **SCR_03 - Scan Receipt & Item Camera (Camera chụp hoá đơn / món đồ):** Điểm vào nhanh nhất, hỗ trợ chụp hoá đơn trực tiếp, tự động nhận diện khung viền, bật/tắt flash, chụp kèm ảnh món đồ.
4. **SCR_04 - OCR Review & Story Attachment (Xác nhận OCR & Ngữ cảnh chi tiêu):** Xem lại kết quả bóc tách từ OCR (tổng tiền, merchant, ngày, dòng hàng), đính kèm ảnh món đồ / cảm xúc, chọn vòng tròn chia sẻ riêng tư.
5. **SCR_05 - Transaction History & Search (Sổ giao dịch & Tra cứu):** Dòng thời gian chi tiêu theo ngày, tra cứu theo tên món đồ, merchant, hóa đơn đính kèm.
6. **SCR_06 - Budget & Expense Control (Ngân sách & Kiểm soát chi tiêu):** Tiến độ chi tiêu từng danh mục, dự báo nguy cơ thâm hụt cuối tháng, đề xuất điều chỉnh không phán xét.
7. **SCR_07 - Shopping Moments & Item Collection (Nhật ký mua sắm & Bộ sưu tập món đồ):** Dạng lưới ảnh (Gallery Grid) lưu giữ các món đồ đã mua, hoá đơn bảo hành, hạn đổi trả và kỷ niệm gắn liền.
8. **SCR_08 - User Settings & Financial Profile (Cài đặt tài khoản & Ví tiền):** Quản lý các nguồn tiền (tiền mặt, thẻ, ví điện tử), thiết lập ngưỡng cảnh báo sớm, quyền riêng tư vòng tròn gia đình/cặp đôi.

---

## 2. Các User Flows chi tiết

### Flow 1: Chụp hoá đơn OCR & Đính kèm khoảnh khắc mua sắm (Smart Capture → Understand → Remember)

- **Điểm bắt đầu:** Người dùng mở ứng dụng và chạm vào nút **Camera trung tâm** tại Home Dashboard (SCR_01).
- **Mục tiêu:** Ghi nhận hoá đơn trong vài giây, tự động trích xuất số tiền/merchant và lưu giữ ảnh món đồ/câu chuyện mua sắm.
- **Điểm kết thúc:** Giao dịch được lưu vào sổ cái, ngân sách tự động cập nhật, món đồ xuất hiện trong Bộ sưu tập (SCR_07).
- **Nhánh lỗi & Phục hồi:** Ảnh chụp bị mờ / thiếu sáng khiến OCR trả về độ tin cậy thấp (Confidence < 80%) ➔ Hệ thống hiển thị cờ cảnh báo màu vàng tại SCR_04, cho phép người dùng kiểm tra, sửa nhanh số tiền hoặc chụp lại mà không làm mất thông tin khác.

```mermaid
flowchart TD
    Start([Bắt đầu: Tại Home Dashboard SCR_01]) --> TapCamera[Chạm nút Camera trung tâm trên Navigation]
    TapCamera --> OpenCamera[Mở màn hình Camera SCR_03]
    OpenCamera --> CaptureReceipt[Chụp hoá đơn hoặc chọn ảnh từ thư viện]
    CaptureReceipt --> OCRProcess[Loading: Hệ thống xử lý ảnh và bóc tách dữ liệu]

    OCRProcess --> CheckConfidence{Độ tin cậy Confidence >= 80%?}

    %% Happy Path
    CheckConfidence -- Đạt (Happy Path) --> ScreenReview[Chuyển sang SCR_04: Điền sẵn Tổng tiền, Ngày, Merchant]

    %% Error Branch & Recovery
    CheckConfidence -- Thấp / Lỗi (Error Branch) --> WarningScreen[SCR_04 hiển thị Banner cảnh báo vàng: 'Ảnh mờ, vui lòng kiểm tra lại số tiền']
    WarningScreen --> UserChoice{Người dùng chọn hướng xử lý?}
    UserChoice -- 'Chụp lại' (Recovery 1) --> OpenCamera
    UserChoice -- 'Sửa tay' (Recovery 2) --> EditAmount[Chạm vào ô Tổng tiền để chỉnh sửa số chính xác]
    EditAmount --> AttachStory

    ScreenReview --> AttachStory[Tùy chọn: Chụp thêm ảnh món đồ & viết cảm xúc ngắn]
    AttachStory --> SelectCategory[Chọn danh mục & Nguồn tiền thanh toán]
    SelectCategory --> TapSave[Bấm 'Lưu khoảnh khắc & Giao dịch']

    TapSave --> SaveDB[(Lưu vào CSDL & Cập nhật Ngân sách)]
    SaveDB --> SyncBudget[Cập nhật số dư & tiến độ ngân sách tức thì]
    SyncBudget --> EndFlow([Kết thúc: Món đồ xuất hiện ở SCR_07, quay về SCR_01])
```

---

### Flow 2: Nhập chi tiêu thủ công & Xử lý cảnh báo vượt ngân sách (Manual Expense & Budget Overrun Warning)

- **Điểm bắt đầu:** Bấm nút **(+) Thêm nhanh** tại Home Dashboard (SCR_01).
- **Mục tiêu:** Ghi nhận khoản chi tiêu tiền mặt nhỏ lẻ không có hoá đơn trong vòng dưới 15 giây.
- **Điểm kết thúc:** Giao dịch được ghi nhận, trạng thái ngân sách được phản ánh trung thực.
- **Nhánh lỗi & Phục hồi:**
  1. _Lỗi nhập liệu:_ Số tiền bằng 0 hoặc để trống ➔ Báo lỗi tại trường nhập liệu, ngăn lưu.
  2. _Cảnh báo nguy cơ:_ Khoản chi khiến ngân sách danh mục vượt 100% ➔ Hiển thị Overlay Dialog cảnh báo thâm hụt sớm và đưa ra lựa chọn phục hồi: "Hủy/Điều chỉnh số tiền" hoặc "Xác nhận khoản chi ngoại lệ có chủ ý".

```mermaid
flowchart TD
    Start([Bắt đầu: Tại Home Dashboard SCR_01]) --> TapAdd[Bấm nút '+' Thêm thủ công]
    TapAdd --> OpenManual[Mở màn hình Add Transaction SCR_02]
    OpenManual --> InputMoney[Nhập số tiền bằng bàn phím số Numpad]
    InputMoney --> ChooseCategory[Chọn nhanh biểu tượng Danh mục]

    ChooseCategory --> ValidateAmount{Số tiền hợp lệ > 0?}
    ValidateAmount -- Không hợp lệ --> ShowInputErr[Hiển thị viền đỏ: 'Vui lòng nhập số tiền lớn hơn 0']
    ShowInputErr --> InputMoney

    ValidateAmount -- Hợp lệ --> TapSubmit[Bấm 'Lưu giao dịch']
    TapSubmit --> BudgetCheck{Khoản chi làm vượt ngân sách danh mục tháng?}

    %% Happy Path: Trong hạn mức
    BudgetCheck -- Không vượt --> SaveNormal[(Lưu giao dịch thành công)]
    SaveNormal --> ReturnDashboard([Về Dashboard SCR_01: Cập nhật số dư])

    %% Warning & Recovery Path
    BudgetCheck -- Vượt ngân sách --> ShowOverrunDialog[Hiển thị Dialog cảnh báo: 'Vượt hạn mức danh mục!']
    ShowOverrunDialog --> UserReaction{Lựa chọn phản hồi của người dùng}

    UserReaction -- 'Hủy / Sửa lại' (Recovery) --> CloseDialog[Đóng dialog, giữ nguyên màn hình SCR_02 để người dùng sửa]
    UserReaction -- 'Xác nhận chi ngoại lệ' (Override) --> ConfirmException[Chấp nhận ghi nhận vượt hạn mức có chủ ý]
    ConfirmException --> SaveNormal
```

---

### Flow 3: Tra cứu hoá đơn & Xem lại kỷ niệm món đồ (Search Receipt & Review Shopping Memory)

- **Điểm bắt đầu:** Người dùng cần tìm lại hoá đơn để kiểm tra bảo hành hoặc hạn đổi trả, bắt đầu tại Tab Lịch sử (SCR_05) hoặc Tab Bộ sưu tập món đồ (SCR_07).
- **Mục tiêu:** Tìm thấy chính xác món đồ và hoá đơn gốc trong vòng dưới 20 giây nhờ bộ lọc ngữ cảnh.
- **Điểm kết thúc:** Mở xem chi tiết hoá đơn gốc, thông tin bảo hành và ảnh món đồ.
- **Nhánh thay thế:** Nếu bộ lọc không tìm thấy kết quả (Empty State) ➔ Cung cấp nút "Đặt lại bộ lọc" để phục hồi danh sách ban đầu.

```mermaid
flowchart TD
    Start([Bắt đầu: Tại Tab Lịch sử SCR_05 hoặc Bộ sưu tập SCR_07]) --> OpenFilter[Bấm thanh tìm kiếm hoặc Bộ lọc Filter]
    OpenFilter --> ApplyFilter[Lọc theo: Có hoá đơn / Khoảng thời gian / Tên Merchant]

    ApplyFilter --> SearchCheck{Tìm thấy kết quả phù hợp?}

    %% Empty State & Recovery
    SearchCheck -- Không có kết quả --> ShowEmpty[Hiển thị Empty State: 'Không tìm thấy giao dịch nào phù hợp']
    ShowEmpty --> TapResetFilter[Bấm nút 'Đặt lại bộ lọc']
    TapResetFilter --> OpenFilter

    %% Happy Path
    SearchCheck -- Có kết quả --> DisplayList[Hiển thị danh sách thẻ món đồ / giao dịch kèm thumbnail ảnh]
    DisplayList --> SelectItem[Chạm vào món đồ cần xem]
    SelectItem --> OpenItemDetail[Mở xem chi tiết tại SCR_07: Xem ảnh món đồ, hoá đơn gốc, ngày mua, hạn bảo hành]
    OpenItemDetail --> ActionShare{Thao tác tiếp theo}
    ActionShare -- 'Xem hóa đơn gốc' --> ZoomReceipt[Phóng to ảnh hoá đơn để đối soát bảo hành]
    ActionShare -- 'Xong' --> CloseDetail([Đóng chi tiết, quay lại danh sách])
```

---

## 3. Bảng ánh xạ Flow sang Màn hình (Screen-to-Flow Mapping Table)

Đảm bảo 100% các màn hình trong danh mục 8 màn hình đều tham gia vào ít nhất một flow hoàn chỉnh:

| Mã Màn Hình | Tên Màn Hình                       |     Flow 1 (Chụp OCR & Khoảnh khắc)      | Flow 2 (Nhập tay & Cảnh báo ngân sách) | Flow 3 (Tra cứu hoá đơn & Kỷ niệm món đồ) |
| :---------- | :--------------------------------- | :--------------------------------------: | :------------------------------------: | :---------------------------------------: |
| **SCR_01**  | Home Dashboard                     |           Điểm bắt đầu (Start)           |        Điểm bắt đầu & Kết thúc         |             Quay về trang chủ             |
| **SCR_02**  | Add Transaction Manual             |                    —                     |             Màn hình chính             |                     —                     |
| **SCR_03**  | Scan Receipt & Item Camera         |        Màn hình chính (Chụp ảnh)         |                   —                    |                     —                     |
| **SCR_04**  | OCR Review & Story Attachment      | Màn hình chính (Xác nhận & Cảnh báo lỗi) |                   —                    |                     —                     |
| **SCR_05**  | Transaction History & Search       |           Xem lại sau khi lưu            |          Xem lại sau khi lưu           |        Điểm bắt đầu tra cứu & Lọc         |
| **SCR_06**  | Budget & Expense Control           |         Tự động đồng bộ số liệu          |   Nguồn kiểm tra hạn mức & Cảnh báo    |           Xem tác động chi tiêu           |
| **SCR_07**  | Shopping Moments & Item Collection |        Điểm kết thúc (Món đồ mới)        |                   —                    |   Điểm hiển thị chi tiết hoá đơn/món đồ   |
| **SCR_08**  | User Settings & Financial Profile  |         Nguồn chọn ví/nguồn tiền         |       Nguồn ngưỡng cảnh báo sớm        |      Cài đặt quyền riêng tư kho ảnh       |
