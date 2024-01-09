# Quá trình khởi động của Linux
### 1. BIOS (Basic Input/Output System) & POST (Power-On Self Test)
- Máy tính bắt đầu quá trình khởi động ngay sau khi bạn bật nguồn điện. Quá trình đầu tiên này được gọi là **post** hoặc **power on self test**. Nếu mọi thứ diễn ra suôn sẻ, quá trình này dẫn đến BIOS. Nếu mọi thứ không êm đẹp, bạn có thể không nghe thấy gì, nghe thấy tiếng "beep" (bíp), hoặc thấy một thông báo lỗi trên màn hình. 

- **BIOS** là một chương trình nhúng trong firmware của máy tính.
	- Tất cả các máy tính Intel x86 sẽ có một hệ thống cơ bản đầu vào/đầu ra hoặc BIOS để phát hiện, xác định và khởi tạo phần cứng. BIOS sau đó tìm kiếm một thiết bị khởi động. Điều này có thể là ổ đĩa mềm, ổ cứng, đĩa CD, thẻ mạng hoặc ổ đĩa USB.

### 2. MBR (Master Boot Record)
- **MBR** là thông tin lưu trữ trong sector đầu tiên của ổ cứng.
- Nó chứa thông tin về nơi GRUB2 được lưu trữ để có thể tải vào RAM của máy tính.

### 3. GRUB2 (Grand Unified Boot Loader v2)
- GRUB2 là bootloader được tải từ MBR vào bộ nhớ RAM.
- Nó cung cấp một menu cho người dùng chọn hệ điều hành hoặc phiên bản cụ thể của Linux để khởi động.
- GRUB2 tải và khởi động kernel Linux.

### 4. Kernel (Nhân)
- **Nhân (Kernel)** là trái tim của hệ điều hành.
- Kernel tải các trình điều khiển cần thiết từ initrd.img (initial ramdisk) vào bộ nhớ.
- Sau đó, nó khởi động quá trình đầu tiên của hệ điều hành, thường là systemd.
### 5. Systemd (PID #1)
- Systemd là một hệ thống khởi động và quản lý tiến trình trong Linux.
- Nó khởi động tất cả các tiến trình cần thiết để hệ thống hoạt động.
- Systemd đọc file /etc/systemd/system/default.target để xác định run-level mặc định để đưa hệ thống vào.
### Run Levels
- Linux có 7 run levels (0 đến 6) mô tả trạng thái khác nhau của hệ thống, ví dụ: 0 là tắt hệ thống, 3 là chế độ đa nhiệm với dòng lệnh, 5 là chế độ đồ họa, và 6 là khởi động lại hệ thống.

Quá trình khởi động của Linux qua các bước này để chuẩn bị và khởi chạy hệ điều hành, cho phép người dùng tương tác với hệ thống một cách hiệu quả.