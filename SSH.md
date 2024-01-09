# SSH Client and Server
- **SSH (Secure Shell)** trong Linux là một giao thức mạng cung cấp cách thức an toàn để truy cập và quản lý các thiết bị từ xa. Nó cung cấp cơ chế mã hóa để bảo vệ thông tin truyền qua mạng.
- Thông qua SSH, người dùng có thể kết nối và làm việc từ xa với máy chủ hoặc thiết bị Linux từ bất kỳ nơi đâu, cho phép thực hiện các tác vụ như đăng nhập, thiết lập kết nối, truyền tệp và thực thi các lệnh từ xa một cách an toàn.
- Một kết nối ssh luôn bắt đầu bằng một bước bắt tay mật mã hóa, tiếp theo là việc mã hóa lớp vận chuyển sử dụng một thuật toán mã hóa đối xứng. Nói cách khác, kênh được mã hóa trước khi bạn bắt đầu nhập bất cứ điều gì.
- Sau đó, quá trình xác thực diễn ra (sử dụng user id/mật khẩu hoặc khóa công khai/tư nhân) và việc truyền thông có thể bắt đầu qua kết nối được mã hóa.
- Giao thức ssh sẽ ghi nhớ các máy chủ mà nó đã kết nối (và cảnh báo bạn trong trường hợp xảy ra điều gì đáng ngờ).

**Public and Private keys**
- **Khóa Công Khai (Public Key)**: Đây là phần của cặp khóa được chia sẻ rộng rãi và được lưu trữ trên máy chủ SSH. Khóa công khai được sử dụng để mã hóa thông tin trước khi gửi đi và cũng được sử dụng để xác thực người dùng. Khóa công khai không bao giờ được giữ bí mật và có thể được chia sẻ một cách an toàn với bất kỳ ai.

- **Khóa Riêng Tư (Private Key)**: Đây là phần của cặp khóa chỉ được lưu trữ trên máy tính cá nhân của người dùng. Khóa riêng tư được sử dụng để giải mã thông tin đã được mã hóa bằng khóa công khai và cũng để xác thực người dùng khi kết nối với máy chủ. Điều quan trọng là giữ cho khóa riêng tư một cách an toàn và không chia sẻ nó với bất kỳ ai.

Quá trình sử dụng khóa công khai và khóa riêng tư trong SSH diễn ra như sau:

1. Người dùng tạo cặp khóa công khai và khóa riêng tư trên máy tính của họ.
2. Khóa công khai được sao chép vào máy chủ mà người dùng muốn kết nối.
3. Khi người dùng kết nối với máy chủ, máy chủ sử dụng khóa công khai để mã hóa một tin nhắn ngẫu nhiên và gửi nó đến người dùng.
4. Người dùng sử dụng khóa riêng tư của mình để giải mã tin nhắn và gửi lại một phản hồi mã hóa cho máy chủ để chứng minh xác thực.
5. Nếu máy chủ có thể giải mã được tin nhắn, nó xác minh xác thực và cho phép người dùng kết nối.

### Đăng nhập vào máy chủ từ xa
- Để đăng nhập vào một máy chủ từ xa sử dụng SSH, bạn cần có thông tin đăng nhập và kết nối mạng đến máy chủ đó. Đầu tiên, mở terminal trên máy tính của bạn và sử dụng lệnh sau:
- Câu lệnh: `ssh username@remote_server_ip`
- Trong đó: 
	- **username** tên người dùng trên máy chủ
	- **remote_server_ip**: địa chỉ ip hoặc tên miền của máy chủ từ xa
- Nhập Mật khẩu Người Dùng: Sau khi nhập lệnh, bạn sẽ được yêu cầu nhập mật khẩu của người dùng trên máy chủ từ xa.
- Xác thực và Đăng Nhập: Sau khi nhập mật khẩu đúng, nếu thông tin đăng nhập hợp lệ, bạn sẽ đăng nhập vào máy chủ từ xa và có thể thực hiện các thao tác từ xa thông qua kết nối SSH.

Nếu máy chủ sử dụng cổng SSH không phải là cổng mặc định (22), bạn có thể chỉ định cổng khi kết nối bằng cách sử dụng -p:
- Câu lệnh: `ssh -p port_number username@remote_server_ip`

Một số tùy chọn phổ biến của lệnh **ssh**:
- **-p port**: Xác định cổng kết nối. Ví dụ: ssh -p 2222 username@remote_server_ip (để kết nối qua cổng 2222).

- **-i key_file**: Sử dụng khóa riêng tư khác thay vì khóa mặc định. Ví dụ: ssh -i /path/to/private_key username@remote_server_ip.

- **-l username**: Xác định người dùng trên máy chủ từ xa. Ví dụ: ssh -l username remote_server_ip.

- **-X**: Kích hoạt chế độ forwarding X11 để chạy các ứng dụng đồ họa từ xa.

- **-v**: Hiển thị thông tin chi tiết (verbose) về quá trình kết nối. Đây có thể giúp khi gặp sự cố kết nối.

- **-N**: Kết nối mà không mở cửa sổ terminal sau khi đăng nhập. Thường được sử dụng khi thiết lập tunnel hoặc chuyển tiếp cổng.

- **-T**: Để chỉ định rằng không cần shell sau khi đăng nhập, thường sử dụng với kết nối tunneling.

- **-C**: Kích hoạt nén dữ liệu trên kết nối SSH.

### sshd
- **sshd** là một phần mềm hoặc dịch vụ trên hệ thống Linux/Unix, đóng vai trò là máy chủ SSH (Secure Shell Server). Nó là daemon (tiến trình chạy nền) chịu trách nhiệm cho việc xử lý kết nối SSH đến hệ thống.
- **sshd** chấp nhận các yêu cầu kết nối từ xa qua giao thức SSH và quản lý việc xác thực người dùng, sau đó cho phép người dùng đăng nhập và sử dụng dịch vụ từ xa vào hệ thống.
- Khi một người dùng từ xa muốn kết nối đến hệ thống thông qua SSH, sshd sẽ nghe (listen) trên cổng mạng SSH (mặc định là cổng 22) và xử lý các yêu cầu kết nối đến từ người dùng, sau đó tiến hành xác thực và cho phép hoặc từ chối kết nối dựa trên thông tin đăng nhập cung cấp.

### sshd keys

