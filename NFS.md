# Network File System (NFS)
Trong Linux, **NFS** là một phần mềm cung cấp khả năng chia sẻ tệp tin và thư mục giữa các máy tính trong một mạng. Đây là cách tuyệt vời để chia sẻ tài nguyên lưu trữ giữa các máy chủ và các máy khách trong mạng nội bộ hoặc qua Internet. NFS cho phép các máy khách truy cập và làm việc trên tệp tin từ xa như chúng được lưu trữ trên máy local.

Lợi ích của NFS:
- **Chia sẻ tập tin và dữ liệu**: NFS cho phép chia sẻ tệp tin và thư mục trên mạng, giúp các máy tính trong mạng truy cập và sử dụng dữ liệu từ máy chủ NFS một cách dễ dàng.

- **Truy cập từ xa và đồng nhất**: Cho phép người dùng truy cập dữ liệu từ xa một cách thuận tiện và đồng nhất. Người dùng có thể truy cập tệp tin từ bất kỳ máy tính nào trong mạng mà không cần phải lưu trữ cục bộ.

- **Tối ưu hiệu suất**: NFS có thể cải thiện hiệu suất truy cập tệp tin trong mạng nội bộ, giúp giảm thời gian truy cập và truyền dữ liệu so với việc sử dụng các phương thức khác như FTP.

- **Quản lý dữ liệu tập trung**: Cho phép quản lý và duy trì tập tin, thư mục tập trung trên máy chủ NFS, giúp dễ dàng thực hiện sao lưu, phục hồi và quản lý dữ liệu.

- **Bảo mật và kiểm soát truy cập**: NFS cung cấp cơ chế kiểm soát truy cập dựa trên quyền hạn, cho phép người quản trị xác định ai có quyền truy cập vào những dữ liệu cụ thể.

- **Tính linh hoạt và mở rộng**: Dễ dàng mở rộng hệ thống bằng cách thêm các máy chủ NFS mới hoặc mở rộng dung lượng lưu trữ mà không gây ảnh hưởng đến sự liên tục của dịch vụ.

**Các cài đặt dịch vụ NFS trên server**

Bước 1: Cài đặt NFS Server
- Câu lệnh: `# yum install nfs-utils`

Bước 2: Xác định thư mục bạn muốn chia sẻ
- Chọn thư mục bạn muốn chia sẻ trên mạng. Ví dụ, thư mục /path/to/your/folder

Bước 3: Cấu hình NFS Server
- Mở file /etc/exports bằng trình soạn thảo văn bản như nano hoặc vi:
	- Câu lệnh: `# vi /etc/exports
- Thêm dòng sau vào cuối file **exports** (thay thế địa chỉ IP hoặc dải IP của client cụ thể và cấp quyền truy cập):
	- `/path/to/your/folder client_IP(rw,sync,no_root_squash)`
- Trong đó: 
	- **/path/to/your/folder** là đường dẫn đến thư mục bạn muốn chia sẻ.
	- **client_IP** là địa chỉ IP hoặc dải IP của máy client được phép truy cập.
	- **rw** cho phép ghi và đọc, **sync** đồng bộ dữ liệu, **no_root_squash** cho phép người dùng root trên client có quyền root trên server.

Bước 4: Khởi động dịch vụ NFS và Firewall
```sh
sudo systemctl enable nfs-server
sudo systemctl start nfs-server
sudo systemctl enable rpcbind
sudo systemctl start rpcbind
sudo systemctl enable nfs-lock
sudo systemctl start nfs-lock
sudo systemctl enable nfs-idmap
sudo systemctl start nfs-idmap
```
