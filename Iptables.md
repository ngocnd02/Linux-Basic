# Iptables
**iptables** là một công cụ quản lý tường lửa mạng mạnh mẽ được sử dụng để quản lý các luật tường lửa trên hệ thống

Chức năng của iptables
- **Kiểm Soát Truy Cập Mạng**: iptables cho phép bạn kiểm soát truy cập mạng bằng cách cho phép hoặc chặn các gói tin dựa trên các tiêu chí như địa chỉ IP nguồn, địa chỉ IP đích, cổng giao thức, giao thức, và nhiều tiêu chí khác.

- **Bảo Vệ Mạng**: Nó cung cấp các biện pháp bảo vệ mạng bằng cách chặn các cuộc tấn công từ xa hoặc ngăn chặn các gói tin có hành vi không mong muốn như SYN-flood hoặc ping of death.

- **Tạo Một Tường Lửa**: Bằng cách sử dụng iptables, bạn có thể tạo và cấu hình một tường lửa mạnh mẽ để bảo vệ hệ thống khỏi các mối đe dọa từ internet hoặc mạng nội bộ.

- **Chuyển Hướng Gói Tin**: iptables cũng cho phép chuyển hướng gói tin, có thể dùng để ánh xạ cổng (port mapping), dẫn hướng gói tin từ một cổng đến cổng khác trên cùng hoặc một máy chủ khác.

- **Kiểm Tra Tình Trạng Giao Tiếp Mạng**: Bạn có thể sử dụng iptables để kiểm tra tình trạng kết nối mạng, xem danh sách các quy tắc hiện tại và các gói tin đang được xử lý.

- **Tạo Các Quy Tắc Mạng Tùy Chọn**: iptables cung cấp khả năng tạo ra các quy tắc mạng tùy chỉnh, cho phép bạn điều chỉnh chi tiết các quy tắc tường lửa dựa trên nhu cầu cụ thể của mạng hoặc ứng dụng.

### Cách cài đặt iptables
Nếu iptables chưa được cài đặt, bạn có thể cài đặt gói iptables-services bằng lệnh sau:
- Câu lệnh: `# yum install iptables-services`
Khởi động dịch vụ iptable: 
- Câu lệnh: `# systemctl start iptables`
Kích hoạt khởi động cùng hệ thống
- Câu lệnh: `# systemctl enable iptables`

![Imgur](https://i.imgur.com/a6Hwmsf.png)
