# Thực hành LVM
#### Thực hiện tạo các PV
- Câu lệnh: `# pvcreate /dev/sdX`

![Imgur](https://i.imgur.com/zsiZt49.png)

#### Thực hiện tạo các VG
- Câu lệnh: `# vgcreate <tên_vg> /dev/sdX`

![Imgur](https://i.imgur.com/WZqkDrW.png)

### Thực hiện tạo các LV
- Câu lệnh: `#lvcreate -n lv_name -L sizeG vg_name`

![Imgur](https://i.imgur.com/Y76JkpB.png)

### Sau đó thực hiện định dạng các LV bằng **mkfs** với loại **ext4** và mount vào các file đã tạo

![Imgur](https://i.imgur.com/JfUP53S.png)

### Cấu hình trong file /etc/fstab để khi reboot lại hệ thống các file mount của lv không bị mất

- Chúng ta dùng các trình soạn thảo như vi để mở /etc/fstab và cấu hình trong file này. 

![Imgur](https://i.imgur.com/sCmHWXT.png)

**Giải thích câu lệnh trong file /etc/fstab**
VD: `/dev/myvg/mylv1 /data   ext4    defaults        0 2`

- **/dev/myvg/mylv1**: Đây là đường dẫn đến Logical Volume (LV) mà bạn gắn kết vào điểm gắn kết /data. Nói cách khác, /dev/myvg/mylv1 là thiết bị lưu trữ dữ liệu cho hệ thống tệp trên /data.

- **/data**: Đây là điểm gắn kết (mount point) của hệ thống tệp. Mọi dữ liệu từ /dev/myvg/mylv1 sẽ hiển thị trong thư mục /data.

- **ext4**: Đây là loại hệ thống tệp được sử dụng trên Logical Volume.

- **defaults**: Các tùy chọn mặc định cho hệ thống tệp. Trong trường hợp này, sử dụng các tùy chọn mặc định.

- **0**: Tham số này đặc tả thứ tự của việc kiểm tra file system khi hệ thống khởi động. Giá trị này thường được sử dụng cho fsck (file system consistency check). Cụ thể:

	- 0: Điều này có nghĩa là không kiểm tra file system trong quá trình khởi động.
	- 1: File system sẽ được kiểm tra trước khi hệ thống được khởi động.
	- 2: File system sẽ được kiểm tra sau khi hệ thống được khởi động, nhưng trước khi các hệ thống tệp không cần kiểm tra.
Trong trường hợp là 0, điều này là  không có kiểm tra file system nào được thực hiện tự động trong quá trình khởi động.

- **2**: Tham số này đặc tả thứ tự của việc sao lưu khi hệ thống khởi động. Giá trị này liên quan đến công cụ dump, một công cụ được sử dụng để sao lưu file system. Cụ thể:
	- 0: Không có sao lưu tự động.
	- 1: Sao lưu trước khi kiểm tra file system.
	- 2: Sao lưu sau khi kiểm tra file system.
Trong trường hợp là 2, điều cho biết rằng file system sẽ được sao lưu sau khi kiểm tra, nếu có.

### Cách giải quyết khi giảm dung lượng của lv. 
- Để có thể tránh mất mát dữ liệu khi giảm dung lượng của LV ta sẽ phải thực hiện sao lưu dữ liệu.
- Ví dụ này thực hiện trên **/dev/myvg/mylv1** và được mount tại thư mục **/data**. Sử dụng câu lệnh **df -h** để kiểm tra

![Imgur](https://i.imgur.com/OsobO0S.png)

- Trước tiên ta tạo 1 thư mục có tên **doucment** bên trong có file **introduction.txt** trong thư mục **/data** để giả sử có tồn tại dữ liệu trong thư mục /data. 

![Imgur](https://i.imgur.com/l52iuNc.png)

![Imgur](https://i.imgur.com/fK25R09.png)

- Và để tránh sự mất mát dữ liệu sau khi giảm dung lượng lv, ta cần sao lưu dữ liệu với **taz**
Câu lệnh: `# taz -czvf mylv1_backup.tar.gz data`
Lệnh trên sẽ tạo một bản sao lưu của dữ liệu trong thư mục /data và lưu vào một tập tin nén mylv1_backup.tar.gz

![Imgur](https://i.imgur.com/j8kCaOX.png)

- Ta tiến hành umount thư mục
Câu lệnh: `umount /data`

- Thực hiện giảm dung lượng 
Câu lệnh: `# lvreduce -L -5G /dev/myvg/mylv1

- Sau đó dùng lệnh resize2fs sẽ điều chỉnh kích thước của hệ thống phản ảnh sự giảm dung lượng của lv
Câu lệnh: `# resize2fs /dev/myvg/mylv1

![Imgur](https://i.imgur.com/ePDytFl.png)

- Ở trên khi ta dùng lệnh **df -h** ta đã thấy kích thước của lv1 là 25G, sau khi thực hiện giảm kích thước của lv đi 5G ta dùng lệnh **lvs** để kiểm chứng xem dung lượng của lv đã được giảm xuống còn 20G

![Imgur](https://i.imgur.com/kUAPQzU.png)

![Imgur](https://i.imgur.com/FOrhRxD.png)

- Sau đó ta tiến hành mount lại /dev/myvg/mylv1 vào thư mục /data  

- Ta thấy xuất hiện lỗi k thể mount lại vào thư mục /data, lúc này ta tiến hành dùng **mkfs** để định dạng lại file hệ thống. Tuy nhiên việc định dạng lại file hệ thống này sẽ khiến lv mất toàn bộ dữ liệu. 

![Imgur](https://i.imgur.com/3hdjis7.png)

![Imgur](https://i.imgur.com/aPzdbxZ.png)

- Sau đó ta thực hiện mount lại
Câu lệnh: mount /dev/myvg/mylv1	/data

![Imgur](https://i.imgur.com/bojr2ZN.png)

- Lúc này ta vào lại thư mục /data và thấy dữ liệu ta tạo đã bị mất. Tuy nhiên ta vẫn còn file nén dữ liệu trước khi thực hiện giảm lv được lưu trong /. giúp ta có thể lấy lại dữ liệu.

![Imgur](https://i.imgur.com/QkvwKuI.png)


**Các trường hợp khi dùng lvreduce có thể không bị mất dữ liệu**

**1.Dung lượng sử dụng của LV không vượt quá dung lượng mới mong muốn**:
Nếu dung lượng sử dụng của LV không vượt quá dung lượng mới bạn muốn thiết lập, bạn có thể giảm dung lượng mà không gặp phải mất dữ liệu.

**2.Dữ liệu trên LV không nằm trong khoảng dung lượng bị giảm**:
Lệnh lvreduce thường chỉ hoạt động nếu không có dữ liệu nằm trong khoảng dung lượng bị giảm. Nếu có dữ liệu nằm trong khoảng đó, bạn sẽ nhận được cảnh báo và phải xác nhận rằng bạn chấp nhận mất dữ liệu.

**Các trường hợp không thể giảm dung lượng của Logical Volume mà không bị mất dữ liệu**

**1.Dữ liệu nằm trong khoảng dung lượng giảm**:
Nếu có bất kỳ dữ liệu nào nằm trong khoảng dung lượng bạn muốn giảm của LV, thì thường không thể giảm dung lượng mà không mất dữ liệu. Việc giảm dung lượng trong trường hợp này sẽ gây mất dữ liệu nằm trong khoảng cắt đi.

**2.Dung lượng mới không đủ để chứa dữ liệu hiện tại**:
Nếu dung lượng mới của LV không đủ để chứa toàn bộ dữ liệu hiện tại, bạn không thể giảm dung lượng mà không làm mất dữ liệu.

**3.Snapshot đang tồn tại**:
Nếu có snapshot tồn tại trên LV, bạn cũng không thể giảm dung lượng của LV gốc. Bạn cần xóa snapshot trước khi thay đổi dung lượng.
