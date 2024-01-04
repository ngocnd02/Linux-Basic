# System Information

**THÔNG TIN VỀ PHIÊN BẢN VÀ HĐH**
1. Xem và thay đổi thông tin hostname của hệ thống
- Câu lệnh: `# hostnamectl`
- Lệnh này sẽ hiển thị thông tin chi tiết về tên máy chủ, icon-name, kernel và nhiều thông tin khác.

![Imgur](https://i.imgur.com/Aysc67P.png)

Để thay đổi hostname, bạn có thể dùng **set-hostname**
- Câu lệnh: `# hostnamectl set-hostname new-hostname#

2. Hiển thị phiên bản của Linux
- Câu lệnh: `# cat /etc/*release`
- Lệnh này sẽ đọc và hiển thị nội dung của các tập tin trong thư mục /etc/ có tên chứa thông tin về phiên bản hệ điều hành.

![Imgur](https://i.imgur.com/LxnLFIG.png)

3. Hiển thị thông tin về kernel của hệ thống.
- Để hiển thị những thông tin về kernel của hệ thống ta sử dụng câu lệnh **uname**
- Câu lệnh: `# uname -a`
- Lệnh này sẽ hiển thị tất cả thông tin chi tiết kernel và hệ thống

![Imgur](https://i.imgur.com/TLhK0cY.png)

- Các tùy chọn khác phổ biến của lệnh **uname**
	- **uname -a**: Hiển thị tất cả các thông tin về kernel, bao gồm tên máy chủ, kernel name, version, release, machine, và platform.

	- **uname -s** hoặc **uname --kernel-name**: Chỉ hiển thị tên kernel.

	- **uname -r** hoặc **uname --kernel-release**: Hiển thị phiên bản của kernel.

	- **uname -v** hoặc **uname --kernel-version**: Hiển thị thông tin về phiên bản kernel và các thông tin mô tả khác.

	- **uname -m** hoặc **uname --machine**: Hiển thị thông tin về kiến trúc của máy (như x86_64 cho máy 64-bit).

	- **uname -o** hoặc **uname --operating-system**: Hiển thị tên hệ điều hành.

**THÔNG TIN VỀ PHẦN CỨNG**
1. Hiển thị thông tin về CPU
- Câu lệnh: ` lscpu`

![Imgur](https://i.imgur.com/Bd1LEah.png)

- Trong đó: 
Architecture: Kiến trúc của CPU (ví dụ: x86_64).
CPU op-mode(s): Chế độ hoạt động của CPU (ví dụ: 32-bit, 64-bit).
Byte Order: Thứ tự byte của CPU (ví dụ: Little Endian, Big Endian).
CPU(s): Số lượng CPU có sẵn trên hệ thống.
Thread(s) per core: Số luồng trên mỗi lõi.
Core(s) per socket: Số lõi trên mỗi socket.
Socket(s): Số lượng socket CPU trên hệ thống.
NUMA node(s): Số lượng NUMA node.
Vendor ID: ID của nhà sản xuất CPU.
CPU family, model, và stepping: Thông tin chi tiết về gia đình, mô hình và bước của CPU.
CPU MHz: Tốc độ xung nhịp của CPU.
CPU max MHz, min MHz: Giá trị tối đa và tối thiểu của tốc độ xung nhịp của CPU.
CPU flags: Các cờ hỗ trợ bởi CPU như SSE, AVX, ...
Virtualization: Hỗ trợ ảo hóa của CPU.
L1/L2/L3 cache: Kích thước của bộ nhớ cache.

2. Liệt kê các thông tin về ổ đĩa và phân vùng.
**df** Hiển thị thông tin về không gian đĩa đã sử dụng và còn trống trên các phân vùng đĩa.
- Câu lệnh : `# df -h`

![Imgur](https://i.imgur.com/nIyBYeB.png)

- Trong đó: 
	- **Filesystem**: Tên hệ thống tập tin hoặc đường dẫn đến phân vùng.
	- **Size**: Kích thước tổng của phân vùng.
	- **Used**: Số lượng không gian đã sử dụng.
	- **Available**: Số lượng không gian còn trống.
	- **Use%**: Phần trăm không gian đã sử dụng so với tổng không gian.
	- **Mounted on**: Đường dẫn mà phân vùng được gắn kết (mounted) vào hệ thống tập tin.

- Các tùy chọn phổ biến của lệnh **df**:
	- **-h, --human-readable**: Hiển thị kích thước dễ đọc cho con người (tính bằng MB, GB, ...).
	- **-T, --print-type**: Hiển thị kiểu hệ thống tập tin của các phân vùng.
	- **-a, --all**: Hiển thị thông tin của tất cả các hệ thống tập tin, bao gồm cả các hệ thống tập tin ảo.
	- **-i, --inodes**: Thay vì hiển thị thông tin về không gian đĩa, hiển thị thông tin về số lượng inode đã sử dụng và còn trống trên phân vùng.

	- **--total**: Hiển thị tổng cộng của tất cả các số liệu.


**lsblk**  Liệt kê các thiết bị lưu trữ và các phân vùng trên hệ thống
- Câu lệnh: `# lsblk`

![Imgur](https://i.imgur.com/lwrb24x.png)

- Trong đó:
	- **NAME**: Tên thiết bị hoặc phân vùng.
	- **MAJ:MIN**: Số hiệu (major và minor) của thiết bị.
	- **RM**: Số thứ tự (đối với các thiết bị có thể gỡ ra, như ổ đĩa USB).
	- **SIZE**: Kích thước của thiết bị hoặc phân vùng.
	- **RO**: Chế độ chỉ đọc (Read-Only) - '0' nếu không, '1' nếu có.
	- **TYPE**: Loại thiết bị hoặc phân vùng (disk, part - phân vùng, rom - đĩa CD/DVD).
	- **MOUNTPOINT**: Đường dẫn nơi thiết bị hoặc phân vùng được gắn kết (mounted) vào hệ thống tập tin.

- Các tùy chọn phổ biến với lệnh **lsblk**
	- **-a, --all**: Hiển thị tất cả các thiết bị, bao gồm cả các thiết bị loop và ram.
	- **-d, --nodep**s: Không hiển thị các thiết bị con (các phân vùng của thiết bị).
	- **-o, --output list**: Chỉ định các cột cụ thể để hiển thị (ví dụ: lsblk -o NAME,SIZE,TYPE,MOUNTPOINT).
	- **-p, --pairs**: Hiển thị đầu ra dưới dạng cặp key-value.
	- **-r, --raw**: Hiển thị dữ liệu nguyên thủy mà không sắp xếp cột theo định dạng ASCII.
	- **-S, --scsi**: Hiển thị thông tin với định dạng SCSI.
	- **-t, --fs**: Hiển thị thông tin về hệ thống tập tin trên các phân vùng.
	- **-h, --help**: Hiển thị trợ giúp về các tùy chọn của lệnh.

![Imgur](https://i.imgur.com/mGWuCD4.png)


**fdisk** Đây là các công cụ dùng để quản lý phân vùng đĩa. Bạn có thể sử dụng chúng để xem thông tin chi tiết về các phân vùng.
- Câu lệnh: `# fdisk -l`
- Trong đó: -l để hiển thị thông tin về các ổ đĩa cùng các phân vùng 

![Imgur](https://i.imgur.com/OjxMoUB.png)

- Trong đó: 
	- **Disk /dev/sdX**: Tên thiết bị ổ đĩa (vd: /dev/sda, /dev/nvme0n1).
	- **Disk identifier**: Định danh duy nhất của ổ đĩa.
	- **Device Boot**: Chỉ định xem phân vùng có khả năng khởi động không.
	- **Start**: Địa chỉ bắt đầu của phân vùng (trong sectors).
	- **End**: Địa chỉ kết thúc của phân vùng (trong sectors).
	- **Sectors**: Số lượng sectors của phân vùng.
	- **Size**: Kích thước của phân vùng.
	- **Type**: Kiểu phân vùng (Linux, NTFS, EFI, v.v.).
	- **Id**: Mã định danh kiểu phân vùng (ví dụ: 83 - Linux, 7 - NTFS).
	- **Boot**: Đánh dấu xem phân vùng có thể khởi động hay không.
	- **System**: Hệ thống tập tin của phân vùng (ví dụ: ext4, swap).

3. Hiển thị thông tin về bộ nhớ RAM
- Câu lệnh: `# free -h`

![Imgur](https://i.imgur.com/f3ndaDE.png)

- Trong đó: 
	- **total**: Tổng dung lượng bộ nhớ RAM và swap.
	- **used**: Dung lượng bộ nhớ đã được sử dụng.
	- **free**: Dung lượng bộ nhớ còn trống và chưa được sử dụng.
	- **shared**: Dung lượng bộ nhớ được chia sẻ giữa các tiến trình.
	- **buff/cache**: Dung lượng bộ nhớ được sử dụng cho bộ đệm (buffer) và bộ nhớ cache. Bộ đệm thường chứa dữ liệu đã được đọc từ đĩa, 	- **trong khi** bộ nhớ cache chứa dữ liệu được sử dụng gần đây.
	- **available**: Dung lượng bộ nhớ có sẵn để sử dụng mà không cần phải swap.

- Các tùy chọn phổ biến của lệnh **free**
	**-b, --bytes**: Hiển thị dung lượng bộ nhớ dưới dạng bytes.
	**-k, --kilo**: Hiển thị dung lượng bộ nhớ dưới dạng kilobytes (KB).
	**-m, --mega**: Hiển thị dung lượng bộ nhớ dưới dạng megabytes (MB).
	**-g, --giga**: Hiển thị dung lượng bộ nhớ dưới dạng gigabytes (GB).
	**-h, --human**: Hiển thị dung lượng bộ nhớ dưới dạng dễ đọc cho con người (ví dụ: KB, MB, GB).
	**-t, --total**: Hiển thị tổng cộng của các số liệu.
	**-s, --seconds <delay>**: Hiển thị thông tin về bộ nhớ sau mỗi khoảng thời gian <delay> giây.
	**-c, --count <count>**: Hiển thị thông tin về bộ nhớ theo số lần lặp lại <count>.

![Imgur](https://i.imgur.com/0yDd3Es.png)


**THÔNG TIN VỀ MẠNG**

1. Hiển thi thông tin về địa chỉ IP và giao diện mạng 
- Câu lệnh: `# ip addr show`
- Lệnh này sẽ hiển thị danh sách các giao diện mạng và các địa chỉ gồm: địa chỉ ip, địa chỉ MAC,..

![Imgur](https://i.imgur.com/RwREk3I.png)

2. Kiểm tra kết nội mạng với một địa chỉ ip hoặc tên miền 
- Câu lệnh: `ping <địa_chỉ_tên_miền>`

![Imgur](https://i.imgur.com/OqziDQa.png)

- Tùy chọn phổ biến của lệnh **ping**
	- **-c <số lần>**: Xác định số lượng gói tin để gửi đi trước khi dừng quá trình ping.
	- **-s <kích thước>**: Chỉ định kích thước gói tin được gửi đi (trong byte).
	- **-i <số giây>**: Thiết lập thời gian chờ giữa các gói tin ping.
	- **-w <thời gian>**: Đặt thời gian chờ để nhận phản hồi (timeout).
	- **-q**: Chế độ im lặng, chỉ hiển thị kết quả cuối cùng sau khi hoàn thành.
	- **-v**: Chế độ verbose, hiển thị thông tin chi tiết hơn về quá trình ping.
	- **-t**: Ping liên tục đến khi bị dừng bằng cách sử dụng Ctrl + C.
	- **-f**: Gửi các gói tin ping với cờ "don't fragment".
	- **-n**: Hiển thị kết quả ping với địa chỉ IP (không thử phân giải tên miền).
	- **-R**: Gửi các gói tin ping có chứa thông tin route.

![Imgur](https://i.imgur.com/l6w30lY.png)

**THÔNG TIN VỀ LOG**
1. Xem log của hệ thống
- Câu lệnh: `# journalctl`

![Imgur](https://i.imgur.com/lHF3esU.png)

