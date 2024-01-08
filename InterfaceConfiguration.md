# Cấu hình NIC trên RHEL 

### /etc/sysconfig/network
- Câu lệnh này dùng để hiển thị nội dung của tệp cấu hình mạng. Nó cho phép chúng ta xác định liệu chúng ta muốn có mạng hay không (NETWORKING = yes), hay hiển thị HOSTNAME hoặc GATEWAY.
- Câu lệnh: `# cat /etc/sysconfig/network`

![Imgur](https://i.imgur.com/9lGEYFr.png)

- Thông số **NOZEROCONF** thường được sử dụng trong cấu hình mạng để vô hiệu hóa Zeroconf (Zero Configuration Networking) trên hệ thống. Zeroconf là một bộ công nghệ mạng tự động hóa cho phép các thiết bị trong một mạng cục bộ tự động cấu hình IP, tìm kiếm tài nguyên mạng và giao tiếp với nhau mà không cần phải cấu hình thủ công.

### /etc/sysconfig/network-scripts/ifcfg-
Thư mục **/etc/sysconfig/network-scripts** chứa các tệp cấu hình cho các giao diện mạng trên hệ điều hành Linux, như CentOS hoặc RHEL. Cụ thể, tệp trong thư mục này thường được đặt tên theo tên của giao diện mạng, ví dụ: ifcfg-eth0, ifcfg-enp0s3, ifcfg-wlan0, tùy thuộc vào tên giao diện mạng cụ thể trên hệ thống.

- Câu lệnh: `# /etc/sysconfig/network-scripts/ifcfg-eth0`
- Câu lệnh này cung cấp tệp cấu hình của giao diện mạng eth0, nó bao gồm các thông số như địa chỉ IP, subnet mask, gateway, DNS, và các thông số mạng khác.

![Imgur](https://i.imgur.com/qd5Dqal.png)

- Trong đó: 
	- **DEVICE**: Tên của giao diện mạng (trong trường hợp này, eth0).

	- **BOOTPROTO**: Phương thức khởi động mạng (như dhcp cho DHCP hoặc static cho địa chỉ IP tĩnh).

	- **IPADDR**: Địa chỉ IP của giao diện.

	- **NETMASK**: Subnet mask của địa chỉ IP.

	- **GATEWAY**: Địa chỉ của gateway mạng.

	- **ONBOOT**: Xác định liệu giao diện sẽ được kích hoạt tự động khi hệ thống khởi động (yes hoặc no).

	- **USERCTL**: Xác định người dùng có quyền điều khiển giao diện không

	- **HWADDR**: Địa chỉ MAC của card mạng

### ifup và ifdown
Lệnh **ifup** và **ifdown** là các công cụ dòng lệnh trong hệ điều hành Linux để kích hoạt (ifup) hoặc ngắt kết nối (ifdown) cho các giao diện mạng.

- **ifup**: Lệnh này được sử dụng để kích hoạt một giao diện mạng cụ thể. Khi chạy ifup cùng với tên của giao diện mạng (ví dụ: ifup eth0), nó sẽ cố gắng kích hoạt kết nối cho giao diện đó.

- **ifdown**: Ngược lại, lệnh này được sử dụng để ngắt kết nối cho một giao diện mạng. Khi chạy ifdown cùng với tên giao diện (ví dụ: ifdown eth0), nó sẽ cố gắng ngắt kết nối và tắt giao diện mạng đó.

### ifconfig
- Lệnh **ifconfig** trong hệ điều hành Linux được sử dụng để hiển thị thông tin về các giao diện mạng trên máy tính.Thông qua **ifconfig**, bạn có thể xem các thông tin cơ bản về các giao diện mạng như địa chỉ IP, subnet mask, địa chỉ MAC, số gói tin đã nhận hoặc gửi qua giao diện đó.
- Câu lệnh: `# ifconfig`

![Imgur](https://i.imgur.com/6pSl8cD.png)

- Trong đó: 

	- **inet addr**: Địa chỉ IP của giao diện mạng.
	- **Bcast**: Địa chỉ broadcast của mạng.
	- **Mask**: Subnet mask của địa chỉ IP.
	- **inet6 addr**: Địa chỉ IPv6 của giao diện mạng.
	- **HWaddr**: Địa chỉ MAC (địa chỉ vật lý) của giao diện.
	- **MTU**: Độ lớn gói tin tối đa mà giao diện có thể chuyển.
	- **RX packets và TX packets**: Số lượng gói tin đã nhận và gửi qua giao diện.
	- **RX errors và TX errors**: Số lượng lỗi nhận và gửi qua giao diện.
	- **RX bytes và TX bytes**: Số lượng byte đã nhận và gửi qua giao diện.

Ngoài ra bạn cũng có thể sử dụng ifconfig để xem thông tin về một giao diện mạng cụ thể:
- Câu lệnh: `# ifconfig eth0`

![Imgur](https://i.imgur.com/nT1vD4D.png)

**Ngoài ra** một công cụ phổ biến hơn có chức năng như lệnh **ipconfig** đó là **ip a**
- Câu lệnh: `# ip a`

![Imgur](https://i.imgur.com/HomMWX9.png)

### arp
Lệnh **arp** trong hệ điều hành Linux được sử dụng để hiển thị hoặc thay đổi bảng ARP (Address Resolution Protocol). Bảng ARP là bảng ghi địa chỉ MAC và địa chỉ IP tương ứng của các thiết bị trong mạng cục bộ.

Lệnh **arp** hữu ích trong việc kiểm tra hoạt động mạng, xác định các thiết bị có kết nối với mạng local, và cũng có thể được sử dụng để giải quyết các vấn đề kết nối mạng bằng cách xóa hoặc thêm vào bảng ARP.

- Câu lệnh: `# arp`

![Imgur](https://i.imgur.com/f8Boh5L.png)

- Các tùy chọn phổ biến của lệnh **arp**:

	- **arp -a hoặc arp -n**: Hiển thị bảng ARP, liệt kê các địa chỉ IP và MAC đã được ghi nhận.

	- **arp -d <địa chỉ IP>**: Xóa một mục từ bảng ARP dựa trên địa chỉ IP cụ thể.

	- **arp -s <địa chỉ IP> <địa chỉ MAC>**: Thêm một mục vào bảng ARP với địa chỉ IP và MAC tương ứng.

	- **arp -i <tên giao diện>**: Xác định giao diện mạng cụ thể khi thực hiện thao tác ARP.

	- **arp -v hoặc arp --verbose**: Hiển thị thông tin chi tiết hơn.

	- **arp -n -d <địa chỉ IP>**: Xóa một mục từ bảng ARP mà không cần xác nhận tên miền (sử dụng địa chỉ IP).

	- **arp -e hoặc arp --device** <tên giao diện>: Hiển thị thông tin từ bảng ARP của giao diện cụ thể.

### route
Lệnh **route** trong hệ điều hành Linux được sử dụng để hiển thị hoặc thay đổi bảng định tuyến, cung cấp thông tin về định tuyến mạng và quản lý các route trên hệ thống. 
- Câu lệnh: `# route`

![Imgur](https://i.imgur.com/rKgXZku.png)

Ngoài ra một lệnh mạnh mẽ và hiện đại hơn so với lệnh **route** là lệnh **ip route**
- Câu lệnh:`# ip route`

![Imgur](https://i.imgur.com/lsaEitd.png)

- Giải thích: 
	- **default via 103.159.51.1 dev eth0**: Đây là route mặc định. Nó cho biết rằng mọi gói tin không khớp với bất kỳ route nào khác sẽ được gửi đến gateway có địa chỉ IP là 103.159.51.1 thông qua giao diện mạng eth0.

	- **103.159.51.0/24 dev eth0 proto kernel scope link src 103.159.51.170**: Đây là một route cụ thể. Nó xác định rằng mọi gói tin có địa chỉ đích thuộc vào mạng con 103.159.51.0/24 sẽ được gửi qua giao diện eth0 và địa chỉ nguồn (src) sẽ là 103.159.51.170. Đây là route nội bộ được tạo bởi kernel (proto kernel) và chỉ có tác dụng trong phạm vi nội bộ của hệ thống (scope link).

	- **169.254.169.254 via 103.159.51.11 dev eth0 proto static**: Đây là một route static. Nó xác định rằng gói tin có địa chỉ IP đích là 169.254.169.254 sẽ được gửi đến gateway có địa chỉ IP là 103.159.51.11 thông qua giao diện mạng eth0.

- Các tùy chọn phổ biến:

	- **ip route show hoặc ip route list**: Hiển thị bảng định tuyến, liệt kê các route mạng.

	- **ip route add <địa chỉ mạng> via <địa chỉ gateway>**: Thêm một route vào bảng định tuyến để định tuyến gói tin đến một mạng cụ thể thông qua một gateway.

	- **ip route del <địa chỉ mạng>**: Xóa một route khỏi bảng định tuyến dựa trên địa chỉ mạng.

	- **ip -6 route show hoặc ip -6 route list**: Hiển thị bảng định tuyến IPv6.

	- **ip route flush**: Xóa tất cả các route trong bảng định tuyến.

	- **ip route get <địa chỉ đích>**: Hiển thị route cụ thể mà gói tin sẽ được chuyển đến để đạt được địa chỉ đích đó.

	- **ip route show table <table-name>**: Hiển thị bảng định tuyến cho một bảng cụ thể.
