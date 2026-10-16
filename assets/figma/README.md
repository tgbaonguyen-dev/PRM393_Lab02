# Figma exports

Export PNG Final UI nằm trong `final-ui/`. Quy ước repository (không phải tên bắt buộc do PDF):

`[screen-id]-[short-name]-[state].png`

Ví dụ: `TX-02-add-expense-error.png`.

Giữ screen ID viết hoa; short-name và state dùng chữ thường, nối bằng `-`, không có khoảng trắng. State mô tả đúng ảnh đã có; đổi tên không xác nhận flow hoặc state đã hoạt động.

| Screen | PNG hiện có |
| --- | --- |
| AU-01 | [Login](final-ui/AU-01-login-default.png) |
| HM-01 | [Default](final-ui/HM-01-home-default.png), [empty](final-ui/HM-01-home-empty.png) |
| TX-01 | [Transaction list](final-ui/TX-01-transaction-list-default.png) |
| TX-02 | [Add expense](final-ui/TX-02-add-expense-default.png), [submitting](final-ui/TX-02-add-expense-submitting.png), [error](final-ui/TX-02-add-expense-error.png) |
| TX-03 | [Transaction detail](final-ui/TX-03-expense-detail-default.png) |
| BD-01 | [Budget dashboard](final-ui/BD-01-budget-dashboard-default.png) |
| BD-02 | [Budget detail](final-ui/BD-02-budget-detail-default.png) |
| BD-03 | [Edit budget](final-ui/BD-03-edit-budget-default.png), [error](final-ui/BD-03-edit-budget-error.png) |
| IN-01 | [Default](final-ui/IN-01-spending-insights-default.png), [empty](final-ui/IN-01-spending-insights-empty.png) |
| EX-01 | [Default](final-ui/EX-01-export-report-default.png), [failed](final-ui/EX-01-export-report-failed.png) |
| NT-01 | [Notification center](final-ui/NT-01-notification-center-default.png) |
| ST-01 | [Profile](final-ui/ST-01-profile-default.png) |

Folder khác: `component-exports/` chứa component exports; `variable-exports/` chứa token exports; `ux/` chứa sơ đồ và wireframe; `prototype-evidence/` chứa bằng chứng prototype. Giữ tên component export như Figma, không ép đổi các tên có khoảng trắng sang tên màn hình.

Chỉ dùng ảnh export Figma thật trong các thư mục trên làm bằng chứng. Accessibility và responsive chưa được xác nhận chỉ từ ảnh export; xem trạng thái kiểm tra trong `design/design-decisions.md`.

