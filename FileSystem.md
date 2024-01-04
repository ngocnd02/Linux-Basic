# File hệ thống 

Hệ thống tập tin của Linux tổ chức theo cấu trúc phân cấp giống như một cây thư mục. Thư mục gốc (root directory) được biểu diễn bằng dấu gạch chéo (/) và là thư mục cao nhất trong cấu trúc tệp hệ thống.

Từ thư mục gốc, các thư mục và tệp tin khác được tổ chức theo cấu trúc phân cấp. Mỗi thư mục có thể chứa các thư mục con và/hoặc các tệp tin. Đường dẫn tuyệt đối đến một tệp tin hoặc thư mục bắt đầu từ thư mục gốc và liệt kê tất cả các thư mục trung gian trên đường đi.

- **/** (Root Directory): Là thư mục cao nhất trong hệ thống tập tin. Tất cả các thư mục và tệp tin khác đều nằm trong thư mục này.
	- Là điểm xuất phát cho mọi đường dẫn tuyệt đối. 

- **/bin** (Binary): Chứa các tệp lệnh cần thiết cho việc khởi động hệ thống và các lệnh cơ bản cho người dùng thông thường.

- **/boot**: Chứa các tệp liên quan đến quá trình khởi động, bao gồm cả các kernel của hệ điều hành.

- **/dev** (Device): Chứa các tệp đại diện cho các thiết bị phần cứng trên hệ thống.

- **/etc** (Etcetera): Chứa các tệp cấu hình của hệ thống và các ứng dụng.
	- Điều chỉnh hành vi của hệ thống. 
	- Tùy chọn các ứng dụng cụ thể, các quy tắc bảo mật.
	- Ví dụ: /etc/passwd và /etc/shadow: Chứa thông tin về người dùng hệ thống và mật khẩu của họ.
	- etc/network/: Chứa cấu hình mạng như các tập tin liên quan đến địa chỉ IP, DNS, cấu hình giao thức mạng.
	- /etc/apache2/ hoặc /etc/nginx/: Chứa cấu hình của máy chủ web Apache hoặc Nginx.


- **/home**: Thư mục cho cá nhân, nơi mà mỗi người dùng có thể có một thư mục con để lưu trữ dữ liệu và tệp cá nhân của họ.
	- Ví dụ: Có một người dùng tên "user1", thư mục cá nhân của họ sẽ nằm trong /home và được gọi là /home/user1. 

- **/lib** và **/lib64** (Library): Chứa các thư viện thực thi cần thiết cho các chương trình trong /bin và /sbin.
	- **/lib**: Cung cấp chức năng cơ bản và hỗ trợ các lệnh cần thiết để hệ thống hoạt động. 
	- **/lib64**: Chứa thư viện cần thiết nhưng dành riêng cho hệ thống 64bit.

- **/mnt** (Mount): Thư mục dùng để kết nối tạm thời với các thiết bị lưu trữ khác như ổ đĩa USB, ổ cứng di động.
	- Gắn kết các thiết bị lưu trữ từ những vùng lưu trữ khác vào hệ thống tệp tạm thời. Khi các thiết bị này được gắn kết vào **/mnt** , người dùng có thể truy cập và làm việc với dữ liệu trong chúng từ hệ thống tệp của mình.

- **/opt** (Optional): Thư mục dành cho các ứng dụng cài đặt thêm.
	- Lưu trữ các gói phần mềm không thuộc quản lý của hệ thống (như các gói phần mềm cài đặt bằng **apt** trong Ubuntu hoặc **yum** trong CentOS).

- **/proc**: Chứa các tệp tin tham chiếu đến thông tin hệ thống, quản lý bởi kernel.
	- Mỗi thư mục và tệp tin trong **/proc** không phải là tệp tin thực tế được lưu trữ trên đĩa cứng mà là các cơ chế mà kernel Linux cung cấp để truy cập và điều khiển thông tin về hệ thống và các tiến trình. 
	- Thông qua **/proc/** có thể truy cập thông tin hệ thống như tài nguyên phần cứng, thông tin về mạng,...

- **/sbin** (System Binary): Chứa các lệnh dành riêng cho quản trị hệ thống.
	- Các lệnh trong **/sbin** thường cần đặc quyền root để chạy và thường được sử dụng để thực hiện các tác vụ quản lý hệ thống như: **ifconfig**, **route**, **fdisk**, **shutdown**, **reboot**,...
	- Thư mục **/sbin** thường không được thêm vào biến môi trường PATH của người dùng thông thường, điều này nhằm ngăn chặn các lệnh quan trọng của hệ thống được sử dụng bởi người dùng không có quyền root

- **/tmp (Temporary)**: Chứa các tệp tạm thời được tạo bởi các chương trình khi chúng đang hoạt động.
	-  Các tệp tin trong thư mục này thường tồn tại trong thời gian ngắn và có thể bị xóa khi hệ thống khởi động lại.

- **/usr** (Unix System Resources): Chứa nhiều chương trình, thư viện, tài liệu và dữ liệu hỗ trợ cho hệ thống.

- **/var** (Variable): Chứa dữ liệu biến thiên như file log (/var/log), dữ liệu cơ sở dữ liệu, email và các tệp tin cache.

# Hệ thống tập tin

Hệ thống tệp (file system) là cách tổ chức và lưu trữ dữ liệu trên các thiết bị lưu trữ như ổ cứng, ổ đĩa SSD, thẻ nhớ, hoặc bất kỳ thiết bị nào có khả năng lưu trữ dữ liệu. Nó bao gồm cách dữ liệu được tổ chức thành tệp và thư mục, cũng như cách hệ thống truy cập, đọc và ghi dữ liệu trên thiết bị lưu trữ đó.

Trong CentOS, hệ thống tệp mặc định thường là XFS hoặc Ext4.
- **XFS**: Đây là một hệ thống tệp mạnh mẽ, hiệu suất tốt và được thiết kế để xử lý các tệp tin lớn. Nó hỗ trợ dung lượng lớn và có khả năng mở rộng tốt. XFS thường được sử dụng cho các ứng dụng yêu cầu lưu trữ lớn như máy chủ tập tin hoặc máy chủ dữ liệu.
- **Ext4**: Là một phiên bản cải tiến của hệ thống tệp Ext3 truyền thống. Nó cung cấp tính năng mở rộng, hiệu suất tốt và ổn định. Ext4 thường được sử dụng cho các hệ thống thông thường và cần một giải pháp lưu trữ ổn định.

Để sử dụng một tệp hệ thống như Ext4 hoặc XFS, bạn cần thực hiện các bước sau:
1. Tạo Phân Vùng với Hệ Thống Tệp Tương Ứng
- Trước tiên, bạn cần tạo một phân vùng trên ổ đĩa hoặc thiết bị lưu trữ mà bạn muốn sử dụng cho hệ thống tệp. Để làm điều này, bạn có thể sử dụng các công cụ như **fdisk**, **parted** hoặc **gparted** để tạo ra một phân vùng và định dạng nó với Ext4 hoặc XFS.
2. Định Dạng Phân Vùng với Hệ Thống Tệp Tương Ứng
- Định dạng với Ext4: 
	- Câu lệnh: `# mkfs.ext4 /đường_dẫn_đến_phân_vùng`
	- Ví dụ: `# mkfs.ext4 /dev/sda1`

- Định dạng với XFS:
	- Câu lệnh: `# mkfs.xfs /đường_dẫn_đến_phân_vùng`
	- Ví dụ: `# mkfs.xfs /dev/sda1`

3. Gắn kết phân vùng vào hệ thống 
Sau khi định dạng, bạn cần gắn kết phân vùng với một thư mục trên hệ thống của bạn để có thể sử dụng được.
- Câu lệnh: 
```sh
mkdir /mnt/mydata
mount /dev/sda1 /mnt/mydata
```
- Sử dụng lệnh mkdir để tạo thư mục mydata, sau đó mount phân vùng /dev/sda1 vào thư mục mydata để sử dụng. 