# Các lệnh cơ bản với hệ thống.
- Lệnh thoát khỏi trạng thái đăng nhập: `# exit`, hoặc `# logout`
## Lệnh khởi động lại hệ thống
- Lệnh **reboot** trong hệ thống Linux được sử dụng để khởi động lại hệ thống máy tính. Dưới đây là một số tùy chọn thường đi kèm với lệnh reboot:
	- reboot: Khởi động lại hệ thống ngay lập tức mà không cần bất kỳ tùy chọn nào khác.
	- reboot -f: Yêu cầu hệ thống khởi động lại ngay lập tức mà không cần đợi các tiến trình hoặc ứng dụng đang chạy lưu trữ dữ liệu của chúng.
	- reboot -h now: Tắt hệ thống ngay lập tức. Tùy chọn này cũng có thể được thực hiện bằng cách sử dụng lệnh halt hoặc poweroff.
	- reboot -t seconds: Cho phép người dùng đặt thời gian trì hoãn trước khi hệ thống khởi động lại (ví dụ: reboot -t 5 sẽ khởi động lại hệ thống sau 5 giây).
	- reboot -d: Chỉ định hệ thống để khởi động lại sau khi hoàn tất kiểm tra quyền truy cập.
## Lệnh hiển thị về các tiến trình đang chạy trên hệ thống. 
- Lệnh `# ps` trong hệ điều hành Unix/Linux được sử dụng để hiển thị thông tin về các tiến trình đang chạy trên hệ thống. Dưới đây là một số tùy chọn thường được sử dụng cùng với lệnh ps:
1. ps: Hiển thị các tiến trình đang chạy của người dùng hiện tại trên terminal hiện tại.
![Imgur](https://i.imgur.com/nrpO38G.png)

Trong đó: 
	- **PID (Process ID)**: ID của tiến trình.
	- **TTY**: Terminal mà tiến trình đang chạy.
	- **TIME**: Thời gian CPU tiêu tốn bởi tiến trình.
	- **CMD**: Tên của lệnh hoặc chương trình.
2. ps -e: Liệt kê tất cả các tiến trình trên hệ thống.

![Imgur](https://i.imgur.com/uiSCWTP.png)
3. ps -ef: Hiển thị thông tin chi tiết về tất cả các tiến trình, bao gồm cả các thông tin về môi trường.
4. ps -aux: Tương tự như ps -ef, nhưng hiển thị một số thông tin thêm về CPU và bộ nhớ (RSS, %CPU, %MEM).
5. ps -u username: Liệt kê các tiến trình của một người dùng cụ thể theo tên người dùng.

## Lệnh được sử dụng để tạm dừng thực thi chương trình trong một khoảng thời gian xác định 
- Lệnh `# sleep <số giây> với <số giây> là thời gian muốn tạm ngừng có thể là số nguyên hoặc số thập phân (tùy chọn), đơn vị là giây.

## Thêm người dùng vào hệ thống
- Sử dụng lệnh: `# useradd <tên_user>`
- Thiết lập mật khẩu cho người dùng: `passwd <tên_user>`
![Imgur](https://i.imgur.com/6SiNdiO.png)
- Sau khi thêm người dùng ta kiểm tra xem trên hệ thống có chưa bằng câu lệnh: `# cat /etc/passwd`
![Imgur](https://i.imgur.com/fc6nwUS.png)

Lệnh này sẽ hiển thị nội dung của tệp /etc/passwd, trong đó chứa thông tin về các người dùng trong hệ thống. Mỗi dòng trong tệp này đại diện cho một người dùng và các thông tin liên quan như tên người dùng, ID người dùng, ID nhóm, thư mục home, shell mặc định, v.v.
- Các tùy chọn phổ biến của lệnh **useradd**

	- -c hoặc --comment: Cho phép bạn thêm một comment hoặc thông tin về người dùng. Thông tin này thường là thông tin mô tả về người dùng.

	- -d hoặc --home: Đặt thư mục home cho người dùng. Thư mục này là nơi mà người dùng sẽ đăng nhập khi họ truy cập vào hệ thống.

	- -g hoặc --gid: Xác định ID nhóm cho người dùng. Người dùng sẽ thuộc nhóm có ID này.

	- -G hoặc --groups: Xác định các nhóm bổ sung mà người dùng sẽ thuộc vào.

	- -s hoặc --shell: Xác định shell mặc định cho người dùng. Shell là môi trường dòng lệnh mà người dùng sẽ sử dụng khi đăng nhập.

	- -u hoặc --uid: Đặt User ID (UID) cho người dùng. Đây là số duy nhất xác định người dùng trong hệ thống.

	- -m hoặc --create-home: Tạo thư mục home cho người dùng nếu nó chưa tồn tại.

	- -e hoặc --expiredate: Xác định ngày hết hạn của tài khoản người dùng. Sau ngày này, tài khoản sẽ không thể đăng nhập được nữa.

** Xóa người dùng **
- Câu lệnh: `# userdel username`
- Nếu muốn xóa cả thử mục người dùng thêm tùy chọn **-r**: `# userdel -r username`
- Các tùy chọn phổ biến của lệnh **userdel**:
	- -r hoặc --remove: Tùy chọn này xóa cả thư mục home của người dùng và dữ liệu liên quan. Nếu không sử dụng tùy chọn này, thư mục home sẽ không bị xóa ngay cả khi người dùng bị xóa.

	- -f hoặc --force: Tùy chọn này buộc xóa người dùng ngay cả khi có các quá trình hoặc phiên đăng nhập đang hoạt động bởi người dùng đó.

** Thay đổi các thuộc tính của người dùng **
Lệnh **usermod** trong Linux được sử dụng để thay đổi các thuộc tính của người dùng đã tồn tại trên hệ thống. Dưới đây là một số tùy chọn phổ biến của lệnh usermod:

- -c, --comment COMMENT: Thêm hoặc chỉnh sửa comment hoặc thông tin mô tả về người dùng.

- -d, --home HOME_DIR: Thay đổi thư mục home của người dùng.

- -g, --gid GROUP: Thay đổi nhóm chính của người dùng.

- -G, --groups GROUPS: Thay đổi các nhóm bổ sung mà người dùng thuộc vào.

- -s, --shell SHELL: Thay đổi shell mặc định của người dùng (shell là môi trường dòng lệnh mà người dùng sử dụng khi đăng nhập).

- -u, --uid UID: Thay đổi User ID (UID) của người dùng.

- -l, --login NEW_LOGIN: Đổi tên đăng nhập của người dùng.

Ví dụ: `# usermod -c "New comment" -d /newhome -g newgroup -G group1,group2 -s /bin/bash -u 1001 -l newusername oldusername`

## Hiển thị các tiến trình đang chạy
- Lệnh top trong Unix/Linux được sử dụng để hiển thị danh sách các tiến trình đang chạy và thông tin về tài nguyên hệ thống như CPU, bộ nhớ, thời gian hoạt động
- Câu lệnh: `# top`

![Imgur](https://i.imgur.com/1SWGblx.png)

Trong đó: 
	- PID (Process ID): ID của tiến trình, mỗi tiến trình có một PID duy nhất.
	- USER: Người dùng sở hữu tiến trình.
	- PR (Priority): Độ ưu tiên của tiến trình, mức độ ưu tiên này được kernel quản lý.
	- NI (Nice value): Giá trị "nice" của tiến trình, thể hiện mức độ ưu tiên khi sử dụng CPU.
	- VIRT (Virtual memory): Tổng lượng bộ nhớ ảo được sử dụng bởi tiến trình.
	- RES (Resident memory): Lượng bộ nhớ thực sự được sử dụng bởi tiến trình.
	- SHR (Shared memory): Lượng bộ nhớ chia sẻ được sử dụng bởi tiến trình.
	- %CPU (CPU utilization): Phần trăm thời gian CPU sử dụng bởi tiến trình từ lần cuối cùng top cập nhật.
	- %MEM (Memory utilization): Phần trăm bộ nhớ RAM được sử dụng bởi tiến trình.
	- TIME+: Tổng thời gian CPU tiêu tốn bởi tiến trình kể từ khi bắt đầu.
	- COMMAND: Tên của lệnh hoặc chương trình đang chạy.
- Các tùy chọn của lệnh top hay sử dụng: 
1. `-d seconds`: Cập nhật màn hình top mỗi số giây được chỉ định. Ví dụ: top -d 5 để cập nhật mỗi 5 giây.
2. `-c`: Hiển thị tên lệnh hoàn chỉnh, không chỉ hiển thị tên tiến trình. Ví dụ: top -c.
3. `-u username`: Chỉ hiển thị các tiến trình của một người dùng cụ thể. Ví dụ: top -u user.
4. `-p PID`: Hiển thị thông tin chỉ với các tiến trình có PID cụ thể. Ví dụ: top -p 1234,5678.
5. `-n number`: Chỉ định số lượng các vòng lặp trước khi top tự đóng. Ví dụ: top -n 10 để chạy top 10 lần và sau đó thoát.
6. `-H`: Hiển thị các tiến trình con (threads) như là các dòng riêng biệt.
7. `-i`: Không hiển thị các tiến trình không hoạt động.
8. `-o field`: Sắp xếp đầu ra theo trường (field) được chỉ định. Ví dụ: top -o +%CPU để sắp xếp theo CPU sử dụng cao nhất.
9. `-b`: Chạy top ở chế độ batch, cho phép xuất đầu ra thành file.

## Đăng nhập bằng tài khoản khác khi vào hệ thống: 
- Để đăng nhập vào một tài khoản người dùng khác trên hệ điều hành Unix/Linux, ta có thể sử dụng lệnh su hoặc sudo tùy thuộc vào cấu hình và quyền hạn của bạn.
- Sử dụng lệnh **su**: `# su - username`
Điền tên người dùng vào phần username. Nếu không nhập tên người dùng cụ thể, su mặc định sẽ đăng nhập vào tài khoản root.
Sau khi nhập lệnh, hệ thống sẽ yêu cầu bạn nhập mật khẩu của tài khoản người dùng đó.