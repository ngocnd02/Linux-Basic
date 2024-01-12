# Cron
- **Cron** là một dịch vụ có sẵn trên hầu hết các hệ thống Linux, cho phép người dùng lập lịch cho các tác vụ để chúng tự động chạy vào các thời điểm cụ thể, như hàng ngày, hàng tuần, hoặc theo các khung thời gian tùy chỉnh.
- Cron hoạt động dựa trên các file cấu hình gọi là "cron jobs" (công việc cron). Các công việc này được lưu trữ trong các file có tên là "crontab" (cron table), mỗi người dùng có một crontab riêng để định nghĩa các công việc cho họ.
- Cú pháp của một crontab thường có dạng: `# * * * * * command_to_execute`
- Trong đó
	- Mỗi dấu * đại diện cho một cột thời gian khác nhau lần lượt là (phút, giờ, ngày, tháng, tuần).
	- command_to_execute là lệnh hoặc tác vụ mà bạn muốn thực hiện

- Ví dụ: `0 9 * * 1 echo "Nội dung email thông báo" | mail -s "Tiêu đề email" user@example.com`

Trong đó:
- **0 9 * * 1**: Đây là phần xác định thời gian chạy cron job.
	- 0: Phút (0 phút).
	- 9: Giờ (9 giờ).
	- *: Ngày trong tháng (mọi ngày).
	- *: Tháng (mọi tháng).
	- 1: Ngày trong tuần (thứ hai, với 0 là Chủ nhật và 6 là Thứ bảy).
- echo "Nội dung email thông báo" | mail -s "Tiêu đề email" user@example.com: Đây là lệnh thực thi bởi cron job.
	- echo "Nội dung email thông báo": In ra thông điệp "Nội dung email thông báo".
	- |: Pipe, dùng để chuyển đầu ra của lệnh trước thành đầu vào của lệnh sau.
	- mail -s "Tiêu đề email" user@example.com: Gửi email với tiêu đề là "Tiêu đề email" tới địa chỉ email user@example.com.

### Để cài đặt và quản lý công việc cron, có thể sử dụng crontab, công cụ dòng lệnh cho phép bạn tạo, chỉnh sửa và xóa các tác vụ cron của một người dùng cụ thể.

Xem **cron** hiện tại:
- Câu lệnh: `# crontab -l`

Chỉnh sửa **crontab**
- Câu lệnh: `# crontab -e`

