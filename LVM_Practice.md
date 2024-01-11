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
Em có 2 cách giải quyết. 
Cách 1: Nén thư mục mà lv mount tới trước khi thực hiện giảm dung lượng của lv, đồng thời unmount trước khi tiến hành giảm dung lượng

![Imgur](https://i.imgur.com/c2po2qf.png)

Cách 2: Tạo snapshot của lv muốn giảm dung lượng, lúc đó ta sẽ tạo ra 1 bản sao của lv trước và tại thời điểm thực hiện snapshot.

![Imgur](https://i.imgur.com/Mqm0gyR.png)
