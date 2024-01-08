# Công cụ khắc phục sự cố
### lsof
**lsof** là một công cụ trong hệ điều hành Unix/Linux, viết tắt của "list open files" (liệt kê các tệp tin đang mở). Nó cho phép người dùng xem danh sách các tệp tin hoặc tài nguyên hệ thống hiện đang được sử dụng hoặc mở bởi các tiến trình đang chạy trên hệ thống.

- Khi được gọi mà không có tùy chọn thì **lsof** sẽ liệt kê tất cả các tệp tin đang mở. 
- Câu lệnh: `# lsof | head `

![Imgur](https://i.imgur.com/XCLRKQz.png)

- Trong đó: 
	- **COMMAND**: Tên của tiến trình hoặc lệnh mà đang sử dụng tài nguyên.

	- **PID**: Process ID, ID của tiến trình mà đang mở tài nguyên.

	- **USER**: Tên người dùng mà tiến trình đó thuộc về.

	- **FD**: File Descriptor, chỉ số của file descriptor đang được sử dụng hoặc kiểu của tài nguyên.

	- **TYPE**: Loại tài nguyên, ví dụ như REG (file), DIR (directory), IPv4 (một kết nối mạng IPv4), và nhiều loại khác.

	- **DEVICE**: Thiết bị hoặc số hiệu inode (iNode number) của tệp tin hoặc tài nguyên.

	- **SIZE/OFF**: Kích thước hoặc vị trí offset của tài nguyên.

	- **NODE**: Số inode của tệp tin hoặc tài nguyên.

	- **NAME**: Tên của tệp tin hoặc tài nguyên.

- Các tùy chọn **lsof** hay sử dụng: 
c <command>: Liệt kê các tệp tin mà các tiến trình của lệnh <command> đang sử dụng.

	- -u <user>: Hiển thị các tệp tin mà người dùng <user> đã mở. Ví dụ:  lsof -u paul | grep home

	- -p <PID>: Liệt kê các tệp tin mà tiến trình có ID là <PID> đang sử dụng.

	- -i: Hiển thị các kết nối mạng mà tiến trình đang sử dụng.

	- -t: Hiển thị thời gian (timestamp) khi tệp tin hoặc tài nguyên được mở.

	- -n: Không resolve địa chỉ IP thành tên máy chủ hoặc tên miền.

	- -a: Hiển thị thông tin chi tiết về các tệp tin (bao gồm cả các tệp mở, tệp đóng, các tệp đã mở từ trước, v.v).

### iostat
**iostat** là một công cụ trong hệ điều hành Linux dùng để theo dõi và hiển thị thông tin về hiệu suất của hệ thống I/O (Input/Output - Nhập/Xuất) như tốc độ đọc/ghi, tình trạng sử dụng các thiết bị lưu trữ (ổ cứng, ổ đĩa SSD, vv) và tình trạng của các bộ đệm.

Khi được chạy mà không có bất kỳ tùy chọn nào, **iostat** sẽ hiển thị thông tin về tốc độ đọc/ghi (ký tự trên giây) cho từng thiết bị lưu trữ trong hệ thống.

- Câu lệnh: `# iostat`

![Imgur](https://i.imgur.com/xiJ8H0m.png)

- Trong đó: 
	- **tps (Transactions per second)**: Số giao dịch hoàn thành trên mỗi giây (số lần đọc hoặc ghi được thực hiện trên thiết bị trong mỗi giây).
	- **kB_read/s**: Tốc độ đọc dữ liệu từ thiết bị (ký tự trên giây).
	- **kB_wrtn/s**: Tốc độ ghi dữ liệu vào thiết bị (ký tự trên giây).
	- **kB_read**: Tổng lượng dữ liệu đã được đọc từ thiết bị (kilobyte).
kB_written: Tổng lượng dữ liệu đã được ghi vào thiết bị (kilobyte).

- Cú pháp có thêm các tùy chọn: `iostat [options] [interval [count]]`
	- **options**: Các tùy chọn để xác định đầu ra cụ thể hoặc chức năng cụ thể.
	- **interval**: Khoảng thời gian giữa các báo cáo (trong giây). Nếu chỉ định, iostat sẽ tạo ra các báo cáo liên tục sau mỗi khoảng thời gian này.
	- **count**: Số lượng báo cáo sẽ được tạo ra trước khi iostat dừng lại. Nếu không chỉ định, nó sẽ tiếp tục tạo báo cáo liên tục.

![Imgur](https://i.imgur.com/mVS5qkN.png)

- Các tùy chọn phổ biến của lệnh **iostat**
	- **-c**: Hiển thị thông tin về sử dụng CPU (tương tự như lệnh mpstat).
	- **-d**: Hiển thị thông tin chi tiết về các thiết bị lưu trữ.
	- **-k**: Hiển thị thông tin theo đơn vị kilobyte (thay vì đơn vị mặc định là byte).
	- **-m**: Hiển thị thông tin theo đơn vị megabyte (thay vì đơn vị mặc định là byte).
	- **-N**: Chỉ định các tên thiết bị lưu trữ cụ thể để theo dõi.

### vmstat
**vmstat** là một công cụ trong hệ thống Linux dùng để hiển thị thông tin về sự sử dụng của bộ nhớ (memory), CPU và swap space. Tên vmstat là viết tắt của "virtual memory statistics". Khi được chạy mà không có tham số, nó hiển thị thông tin tổng quan về sự sử dụng tài nguyên hệ thống.
- Câu lệnh: `vmstat [options] [delay [count]]`
- Trong đó: 
	- **options**: Các tùy chọn để hiển thị thông tin cụ thể (ví dụ: -a, -d, -s).
	- **delay**: Khoảng thời gian giữa các báo cáo (trong giây).
	- **count**: Số lượng báo cáo sẽ được tạo ra trước khi vmstat dừng lại. Nếu không chỉ định, nó sẽ tiếp tục tạo báo cáo liên tục.

- Thông tin chính mà vmstat cung cấp bao gồm:
	- **Procs**: Số lượng tiến trình và thông tin về việc xử lý các tiến trình.
	- **Memory**: Thông tin về sử dụng bộ nhớ và swap.
	- **Swap**: Thông tin về sử dụng không gian swap.
	- **IO**: Thống kê về hoạt động đọc/ghi trên đĩa.
	- **System**: Thông tin về hệ thống và kernel.
	- **CPU**: Thống kê về sử dụng CPU.
	- **r**: Số tiến trình đang chạy (running).
	- **b**: Số tiến trình đang bị chặn (blocked).
	- **swpd**: Số lượng bộ nhớ đã được sử dụng trong phần swap.
	- **free**: Số lượng bộ nhớ không được sử dụng.
	- **buff**: Số lượng bộ nhớ được sử dụng cho các dữ liệu buffer.
	- **cache**: Số lượng bộ nhớ được sử dụng cho cache.
	- **si**: Số lượng dữ liệu được ghi từ RAM vào swap space (swap in).
	- **so**: Số lượng dữ liệu được ghi từ swap space vào RAM (swap out).
	- **bi**: Số lượng block dữ liệu được ghi từ thiết bị đọc vào RAM.
	- **bo**: Số lượng block dữ liệu được ghi từ RAM ra thiết bị.
	- **in**: Số lượng truy cập (interrupts) vào kernel mỗi giây.
	- **cs**: Số lượng context switches (chuyển đổi ngữ cảnh) mỗi giây.
	- **us**: Tỷ lệ thời gian CPU sử dụng cho các tiến trình người dùng.
	- **sy**: Tỷ lệ thời gian CPU sử dụng cho các tiến trình hệ thống.

![Imgur](https://i.imgur.com/Ws0sEkd.png)


