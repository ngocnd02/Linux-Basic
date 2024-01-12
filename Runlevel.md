#Runlevel
**Runlevel** là một khái niệm trong hệ thống Linux, chỉ định trạng thái hoạt động hiện tại của hệ thống. Mỗi runlevel tương ứng với một tập hợp các dịch vụ và chế độ hoạt động khác nhau của hệ thống.

Trong hệ thống Linux sử dụng hệ thống quản lý dịch vụ SysVinit, các runlevel thông thường được sử dụng bao gồm:
- **Runlevel 0**: Chế độ tắt hoặc shutdown. Hệ thống sẽ dừng hoàn toàn.
- **Runlevel 1 hoặc S**: Chế độ đơn người dùng (single user mode). Thường được sử dụng để sửa chữa và bảo trì hệ thống.
- **Runlevel 2**: Chế độ đa người dùng với mạng. Thường tương đương với runlevel 3 nhưng không chạy dịch vụ NFS.
- **Runlevel 3**: Chế độ đa người dùng với mạng. Là runlevel mặc định cho môi trường máy chủ không có giao diện đồ họa.
- **Runlevel 4**: Thường không được sử dụng và có thể được người dùng tùy chỉnh.
- **Runlevel 5**: Chế độ đa người dùng với giao diện đồ họa (graphical user interface - GUI). Đây là runlevel mặc định cho nhiều hệ thống desktop.
- **Runlevel 6**: Chế độ khởi động lại hệ thống.

### Để xem runlevel hiện tại của hệ thống, có thể sử dụng lệnh **runlevel**:
- Câu lệnh: `# runlevel`

![Imgur](https://i.imgur.com/jcrDkxy.png)

### Thay đổi các chế độ runlevel trong hệ thống
Trong CentOS có thể thay đổi **runlevel** bằng cách sử dụng câu lệnh init hoặc systemctl tùy thuộc vào phiên bản cụ thể và cách thức quản lý dịch vụ.
**Sử dụng câu lệnh init**
- Ví dụ, để chuyển từ runlevel 3 (đa người dùng với mạng) sang runlevel 5 (đa người dùng với giao diện đồ họa), bạn có thể nhập lệnh:
- Câu lệnh: `# init 5`

**Sử dụng systemctl**
- Ví dụ, để chuyển từ môi trường đa người dùng sang môi trường đồ họa, bạn có thể sử dụng:
- Câu lệnh: `sudo systemctl isolate graphical.target`


# Systemd
**Systemd** là một hệ thống khởi động và quản lý dịch vụ (init system) trong hệ điều hành Linux. Nó là một trong những thành phần quan trọng của nhiều bản phân phối Linux hiện đại.

Công dụng chính của systemd:

- Khởi động hệ thống: systemd thay thế init system truyền thống trong Linux và quản lý quá trình khởi động của hệ thống. Nó có thể thực hiện các tác vụ khởi động song song, tối ưu hóa và tăng tốc quá trình khởi động.

- Quản lý dịch vụ: systemd quản lý các dịch vụ (services) trong hệ thống. Nó cho phép bạn khởi động, dừng, restart các dịch vụ, kiểm tra trạng thái của chúng và tự động khởi động các dịch vụ cần thiết khi hệ thống khởi động.

- Quản lý tiến trình: Ngoài quản lý dịch vụ, systemd cũng quản lý các tiến trình (processes) khác trong hệ thống, cung cấp thông tin chi tiết về tiến trình đang chạy.

- Quản lý logs: systemd cung cấp systemd-journald, một công cụ quản lý logs mạnh mẽ để theo dõi và phân tích logs từ các dịch vụ và tiến trình.

- Quản lý cgroups: systemd sử dụng các nhóm điều khiển (cgroups) để quản lý tài nguyên hệ thống như CPU, bộ nhớ, và các tài nguyên khác.


