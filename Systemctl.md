# Systemctl
**Systemctl** là một công cụ quản lý dịch vụ (service) trên hệ thống Linux. Nó được sử dụng để kiểm soát các dịch vụ, các quá trình (processes) và các đơn vị (units) của hệ thống init (init system). Systemctl cho phép người dùng thực hiện các hoạt động như khởi động, dừng, khởi động lại, kiểm tra trạng thái của các dịch vụ, cũng như xem logs và quản lý các thành phần khác của hệ thống.

Nó thường được sử dụng để thay thế cho các lệnh cũ như service trên một số bản phân phối Linux mới, như systemd-based Linux distributions (ví dụ: Ubuntu từ phiên bản 15.04 trở đi, CentOS/RHEL từ phiên bản 7 trở đi).

Cú pháp cơ bản khi sử dụng systemctl:

- **Khởi động dịch vụ**: sudo systemctl start <tên_dịch_vụ>
- **Dừng dịch vụ**: sudo systemctl stop <tên_dịch_vụ>
- **Khởi động lại dịch vụ**: sudo systemctl restart <tên_dịch_vụ>
- **Kiểm tra trạng thái của dịch vụ**: sudo systemctl status <tên_dịch_vụ>
- **Bật dịch vụ để khởi chạy cùng hệ thống**: sudo systemctl enable <tên_dịch_vụ>
- **Tắt dịch vụ không khởi chạy cùng hệ thống**: sudo systemctl disable <tên_dịch_vụ>