# File Permissions
File permissions trong Linux quy định quyền truy cập và điều khiển người dùng, nhóm và các quyền khác liên quan đến file hoặc thư mục. Mỗi file hoặc thư mục có ba loại quyền cơ bản:

1. **Read (đọc - r)**: Cho phép xem nội dung của file hoặc thư mục. Với thư mục, quyền này cho phép đọc danh sách các file và thư mục trong đó.
2. **Write (ghi - w)**: Cho phép chỉnh sửa hoặc viết vào file hoặc thư mục. Với thư mục, quyền này cho phép thay đổi nội dung (tạo, xóa, đổi tên file hoặc thư mục).
3. **Execute (thực thi - x)**: Cho phép thực thi file nếu là file thực thi (executable file), hoặc truy cập vào thư mục để làm việc với nó.

Các quyền này được áp dụng cho ba nhóm người dùng:

1. **Chủ sở hữu (Owner)**: Người dùng mà file hoặc thư mục thuộc về.
2. **Nhóm (Group)**: Nhóm mà file hoặc thư mục thuộc về. Tất cả thành viên trong nhóm này có quyền truy cập như nhau.
3. **Khác (Others)**: Tất cả các người dùng còn lại không thuộc nhóm trên.

Quyền truy cập được hiển thị trong terminal khi sử dụng lệnh `ls -l` và sẽ hiển thị một chuỗi ký tự như `-rwxr-xr--`, trong đó:

- **r** là read (đọc).
- **w** là write (ghi).
- **x** là execute (thực thi).
- **-** có thể là khoảng trống, hoặc là một dấu hiệu không có quyền.

## Thay đổi người và nhóm người sở hữu file

Để thay đổi người và nhóm người sở hữu của một file trong Linux, bạn có thể sử dụng lệnh **chown** để thay đổi người sở hữu và **chgrp** để thay đổi nhóm người sở hữu.

Thay đổi người sở hữu 
- Câu lệnh: `# chown new_owner_name file_name`

![Imgur](https://i.imgur.com/z6j35De.png)

Thay đổi nhóm sở hữu
- Câu lệnh: `# sudo chgrp new_group_name file_name`

![Imgur](https://i.imgur.com/U4iJuoq.png) 

- Cách 2: vẫn sử dụng lệnh chown

![Imgur](https://i.imgur.com/KqiutZO.png)

- Hoặc để thay đổi cả hai: 

![Imgur](https://i.imgur.com/KTT3efe.png) 


## Thay đổi quyền truy cập file 
Để thay đổi quyền truy cập của file trong Linux, bạn sử dụng lệnh **chmod (change mode)**. Lệnh này cho phép bạn thay đổi quyền truy cập theo ba loại quyền cơ bản: đọc (r), ghi (w), và thực thi (x).

Mỗi file được quản lý bởi 3 đối tượng: 
- User onwer: u
- Group onwer: g
- Others: o

Thay đổi quyền truy cập theo ký tự biểu diễn: 
- Phân quyền: 
	- **+**: Thêm quyền.
	- **-**: Loại bỏ quyền.
	- **=**: Đặt quyền chính xác.
- Câu lệnh: `# chmod u+rwx,g+rx,o+r file_name`
Trong đó: 
	- **u+rwx**: Thêm quyền đọc, ghi và thực thi cho người sở hữu.
	- **g+rx**: Thêm quyền đọc và thực thi cho nhóm sở hữu.
	- **o+r**: Thêm quyền đọc cho người dùng khác.

![Imgur](https://i.imgur.com/5MaPM72.png)

Thay đổi quyền truy cập theo số nguyên biểu diễn
- Trong thay đổi quyền theo số, ta cần biết
	- Quyền **read (r)** có giá trị là 4
	- Quyền **write (w)** có giá trị là 2
	- Quyền **execute (x)** có giá trị là 1

- Câu lệnh :`# sudo chmod 755 file_name`
Trong đó: 
	- 7: Quyền đọc, ghi và thực thi cho người sở hữu.
	- 5: Quyền đọc và thực thi cho nhóm sở hữu.
	- 5: Quyền đọc và thực thi cho người dùng khác.

![Imgur](https://i.imgur.com/BGgVurh.png)


Các tùy chọn phổ biến: 
-c ( --changes): Hiển thị thông báo chỉ khi quyền truy cập thực sự được thay đổi.
Ví dụ: chmod -c u+rwx file.txt

-f ( --silent, --quiet): Không hiển thị thông báo lỗi khi có vấn đề xảy ra.
Ví dụ: chmod -f u+rwx file.txt

-v ( --verbose): Hiển thị thông báo chi tiết cho mỗi file được thay đổi quyền truy cập.
Ví dụ: chmod -v u+rwx file.txt
