# Tìm kiếm file
Các công cụ tìm kiếm được sử dụng để tìm file trên hệ thống: 
- **locate**- Tìm kiếm file theo tên
- **find**- Tìm kiếm các tập tin trong một hệ thống phân cấp thư mục 

### locate
Lệnh **locate** thực hiện một tìm kiếm cơ sở dữ liệu nhanh chóng của các đường dẫn tệp và sau đó xuất ra tất cả các tên phù hợp với một chuỗi con cụ thể đã cho.
Cho ví dụ, chúng ta muốn tìm tất cả các chương trình có tên bắt đầu bằng "zip". Vì chúng ta đang tìm kiếm các chương trình, có thể giả định rằng tên của thư mục chứa các chương trình sẽ kết thúc bằng "bin/"
- Câu lệnh: `# locate bin | grep zip`
- Lệnh này tìm kiếm trong cơ sở dữ liệu của locate tất cả các đường dẫn chứa từ "bin" và sau đó lọc kết quả này để chỉ hiển thị những dòng chứa từ "zip" bằng grep

![Imgur](https://i.imgur.com/baT7ieu.png)

- Các tùy chọn phổ biến của lệnh **locate**
	- **-i, --ignore-case**: Cho phép tìm kiếm không phân biệt chữ hoa chữ thường.
	- **-c, --count**: Chỉ hiển thị số lượng kết quả thay vì danh sách các tệp tin.
	- **-l, --limit**: Xác định số lượng kết quả tối đa để hiển thị.
	- **-b, --basename**: Chỉ tìm kiếm dựa trên tên tệp, bỏ qua đường dẫn.
	- **-S, --statistics**: Hiển thị thống kê về cơ sở dữ liệu locate, bao gồm thông tin về thời gian cập nhật gần nhất.

### find
Trong khi chương trình **locate** có thể tìm thấy một tệp chỉ dựa trên tên của nó, chương trình **find** tìm kiếm trong một thư mục cụ thể (và các thư mục con của nó) các tệp tin dựa trên nhiều thuộc tính khác nhau

- Cú pháp cơ bản: `# find /đường/dẫn/tìm/kiếm -option(s) pattern`
- Ví dụ: `# find . -name intro.txt`
- Lệnh này sẽ tìm kiếm tất cả các tệp có tên là "intro.txt" trong thư mục hiện tại (.) và trong các thư mục con của nó. Nếu có bất kỳ tệp nào cùng tên này hoặc mẫu tên tương tự, chúng sẽ được liệt kê ra trong kết quả.

![Imgur](https://i.imgur.com/twFrqyr.png)

- Một số tùy chọn phổ biến: 
	- **-name**: Tìm kiếm theo tên của tệp hoặc thư mục.
	- **-type**: Tìm kiếm theo loại của đối tượng (d: thư mục, f: tệp thực thể, l: liên kết, v.v.).
	- **-size**: Tìm kiếm theo kích thước của tệp.
	- **-mtime, -atime, -ctime**: Tìm kiếm theo thời gian sửa đổi (-mtime), thời gian truy cập (-atime), và thời gian thay đổi inode (-ctime).
	- **-exec**: Thực thi một lệnh trên mỗi kết quả tìm kiếm.


