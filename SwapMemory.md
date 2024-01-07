# Swap memory
### 1. Swap memory là gì?
- **Swap memory** được sử dụng để bổ sung cho bộ nhớ vật lý (RAM). Khi RAM của máy tính đã đầy hoặc cạn kiệt do sử dụng quá nhiều ứng dụng hoặc quá trình, hệ điều hành có thể sử dụng swap memory để lưu trữ dữ liệu tạm thời, giải phóng RAM cho các ứng dụng khác.

- **Swap memory** thường là một phần trên ổ cứng được cấu hình để hoạt động như bộ nhớ ảo. Khi RAM đầy, dữ liệu không còn được sử dụng thường xuyên sẽ được chuyển từ RAM sang swap memory để tạo không gian cho các ứng dụng và quá trình khác cần sử dụng RAM.

- Tuy nhiên, việc sử dụng swap memory có thể làm giảm hiệu suất hệ thống do tốc độ truy cập dữ liệu trên ổ cứng thấp hơn nhiều so với RAM. Khi hệ thống phải thường xuyên truy cập swap memory để lấy dữ liệu trở lại RAM, điều này có thể gây chậm trễ và làm giảm trải nghiệm người dùng.

### 2. Tạo Swap File
**Tạo một file sử dụng làm swap**
- Câu lệnh: `# fallocate -l 2G /mnt/swapfile`
- Câu lệnh này tạo một file với kích thước cụ thể là 2G và đặt tên là swapfile trong thư mục /mnt
- Trong đó: 
	- **fallocate** Là một công cụ trong hệ thống Linux dùng để cấp phát không gian cho file.
	- **-l 2G** chỉ định dung lượng cho file mới được tạo là 2GB
	- Lưu ý: khi sử dụng **fallocate** để tạo file swap, không có dữ liệu nào thực sự được ghi vào file này ngay lập tức. Thay vào đó, không gian trống được cấp phát trên ổ đĩa để sử dụng khi cần thiết, và file sẽ chứa dữ liệu khi swap được kích hoạt để lưu trữ thông tin từ RAM khi RAM đầy.

- Các tùy chọn phổ biến đi cùng lệnh **fallocate**
	- **-l, --length**: Sử dụng để chỉ định kích thước của file mới. Ví dụ: -l 1G sẽ tạo một file có dung lượng 1GB.

	- **-o, --offset**: Cho phép bạn chỉ định vị trí bắt đầu cấp phát không gian trong file hiện có. Đây không phải là tùy chọn thường xuyên được sử dụng khi tạo swap file.

	- **--keep-size**: Tạo file với dung lượng được chỉ định nhưng không cấp phát không gian thực tế cho file ngay lập tức. Tùy chọn này có thể hữu ích khi bạn muốn giữ trước kích thước của file nhưng chỉ cấp phát không gian khi cần thiết sau này.

	- **--punch-hole**: Xóa không gian không cần thiết từ file. Điều này cho phép giảm dung lượng thực tế của file mà không cần xóa file hoặc di chuyển dữ liệu.

	- **--dig-holes**: Tạo ra các "lỗ" (holes) trong file, là không gian không cần thiết không chiếm dung lượng thực tế trên ổ đĩa. Điều này thường được sử dụng để tạo file sparse (thưa) để tiết kiệm dung lượng đĩa.

**Định dạng file swap**
- Câu lệnh: 
	```sh
	chmod 600 /mnt/swapfile
	mkswap /mnt/swapfile
	```
- Câu lệnh `chmod 600 /mnt/swapfile` sử dụng **chmod** để đặt quyền cho file, ở đây 600 có nghĩa chỉ có chủ sử hữu mới có quyền đọc và ghi file, còn lại không ai có quyền truy cập file này
- Câu lệnh `mkswap /mnt/swapfile` sử dụng **mkswap** để định dạng một file để sử dụng như swap space.

**Kiểm tra swap đã hoạt động hay chưa**
- Câu lệnh: `# swapon --show`

- Các tùy chọn phổ biến của **swapon**:
	- **-a, --all**: Kích hoạt tất cả các phân vùng hoặc tệp swap được chỉ định trong /etc/fstab.

	- **-s, --summary**: Hiển thị thông tin tổng quan về các phân vùng hoặc tệp swap đang hoạt động.

	- **-v, --verbose**: Hiển thị thông tin chi tiết về quá trình kích hoạt swap.

![Imgur](https://i.imgur.com/189NIWz.png)


### 3. Tạo Swap Partition

**Sử dụng công cụ quản lý ổ đĩa (như fdisk hoặc parted) để tạo partition mới có loại là swap**
- Câu lệnh: `# fdisk /dev/sdX`

Tạo một partition mới
- Nhấn **n** và chọn loại **p** (primary partition) hoặc **e** (extended partition) tùy thuộc vào loại phân vùng bạn muốn tạo.
- Chọn số thứ tự cho partition (ví dụ: 1).
- Chọn dung lượng cho partition swap (ví dụ: nhập +42 để tạo partition 2GB).

Đặt loại của partition là 82 (Linux swap)
- Nhấn **t** để thay đổi loại cua partition
- Chọn số thứ tự của partition đã tạo (ví dụ: 1).
- Nhập 82 để đặt loại là Linux swap.

**Định dạng partition mới thành swap**
- Câu lệnh: `# mkswap /dev/sdX1`

**Kích hoạt swap partition**
- Câu lệnh: `# swapon /dev/sdX1`

### 4. Xóa file swap

**Vô hiệu hóa swap**
- Câu lệnh: `# swapoff /mnt/swapfile`

**Xóa swap file**
- Câu lệnh: `# rm /mnt/swapfile`

**Loại bỏ thông tin swap trong /etc/fstab (nếu cần)**
Nếu thông tin về swap file đã được thêm vào file /etc/fstab để tự động kích hoạt sau khi khởi động, bạn cũng nên loại bỏ dòng liên quan đến swap file trong file này.

Mở file /etc/fstab với trình soạn thảo văn bản như nano hoặc vi.Tìm và xóa dòng chứa đường dẫn đến swap file. Sau khi xóa, lưu lại và đóng file.
