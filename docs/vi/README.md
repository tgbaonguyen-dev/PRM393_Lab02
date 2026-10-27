# Tài liệu dự án Expense Tracker

> English version: [../en/README.md](../en/README.md).

Thư mục này là điểm bắt đầu để đọc tài liệu của dự án. Nội dung được sắp theo luồng từ yêu cầu môn học đến nghiên cứu người dùng và đặc tả sản phẩm.

## Thứ tự đọc

1. [Yêu cầu PRM323 Lab 2](requirements/lab2.md): phạm vi, deliverable và checklist nộp bài.
2. [Tổng quan persona](research/personas/README.md): nhóm người dùng, vấn đề và ba proto-persona.
3. [Expense Tracker SRS](requirements/expense-tracker-srs.md): phạm vi sản phẩm, business rules, FR, NFR, data model và acceptance criteria.
4. [Information Architecture](ux/information-architecture.md): cấu trúc điều hướng, screen catalogue và quan hệ giữa các màn hình.
5. [User Flows](ux/user-flows.md): ba luồng chính, nhánh thay thế và cách phục hồi.

Mỗi tài liệu tiếng Việt có bản tiếng Anh đối chiếu qua liên kết ngay đầu file. Hai ngôn ngữ được tách thành hai cây thư mục đối xứng `docs/vi/` và `docs/en/`.

## Cấu trúc hiện tại

```text
docs/
├── vi/
│   ├── README.md
│   ├── requirements/
│   ├── research/personas/
│   └── ux/
└── en/
    ├── README.md
    ├── requirements/
    ├── research/personas/
    └── ux/
```

## Quyền sở hữu nội dung

| Chủ đề | Nguồn chính |
| --- | --- |
| Điều kiện và deliverable của bài lab | `requirements/lab2.md` |
| Hành vi, nghiệp vụ và tiêu chí nghiệm thu của app | `requirements/expense-tracker-srs.md` |
| Persona | `research/personas/` |
| Các bản dịch tiếng Anh | Cây thư mục đối xứng trong `../en/` |
| Information architecture và screen catalogue | `ux/information-architecture.md` |
| Ba user flow và flow-to-screen matrix | `ux/user-flows.md` |

Bản tiếng Việt là nguồn chính cho toàn bộ tài liệu song ngữ. Khi nội dung thay đổi, cập nhật bản tiếng Việt trước rồi đồng bộ bản tiếng Anh; không thay đổi các requirement ID, flow ID, screen ID, enum, field hoặc công thức khi dịch.

## Tài liệu sẽ bổ sung theo tiến độ

Các tài liệu sau chỉ được tạo khi nhóm thực hiện đến đúng bước và có bằng chứng thật:

- AI design log và bằng chứng Google Stitch.
- Design specification cho token, component, state, content tone và responsive behavior.
- Design decisions và accessibility evidence.
- Screen specification.
- Flutter handoff.

Không tạo placeholder hoặc log hồi tố chỉ để hoàn thiện cây thư mục.
