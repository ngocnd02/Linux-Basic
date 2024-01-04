# Backup data
Để sao lưu dữ liệu trong Linux, có một số cách thức và công cụ khác nhau bạn có thể sử dụng. 

**rsync** là một công cụ mạnh mẽ trong Linux dùng để sao chép và đồng bộ dữ liệu giữa các thư mục, thư mục cục bộ và từ xa, hoặc giữa các máy chủ khác nhau.
- Câu lệnh: `# rsync [tùy_chọn] nguồn đích
1. Sao chép từ một thư mục đến một thư mục khác trên cùng một máy
- Câu lệnh: `# rsync -av /nguồn /đích`
- Trong đó: 
	- **-a**(archive mode) Chế độ sao lưu theo kiểu archive, bao gồm đồng bộ hóa tất cả các thuộc tính
	- **-v**(verbose) để hiển thị thông tin chi tiết về quá trình sao chép.

![Imgur](https://i.imgur.com/abvHcUG.png)

2. Sao lưu từ một máy đến máy khác thông qua SSH
- Câu lệnh: rsync -avh -e "ssh -i /đường/dẫn/đến/khoá/riêng" /đường/dẫn/nguồn username@địachost:/đường/dẫn/đích
- Trong đó: 
	- **-a**: Chế độ sao lưu theo kiểu archive, bao gồm đồng bộ hóa tất cả các thuộc tính.
	- **-v**: Hiển thị chi tiết khi đang sao chép dữ liệu.
	- **-h**: Hiển thị kích thước dữ liệu ở định dạng dễ đọc.
	- **-e**  "ssh -i /đường/dẫn/đến/khoá/riêng": Sử dụng SSH và cung cấp đường dẫn đến khóa riêng để kết nối.

Các tùy chọn phổ biến của rsync
1. **-v, --verbose**: Hiển thị thông tin chi tiết về quá trình sao chép.

2. **-a, --archive**: Chế độ lưu trữ, bảo tồn các thuộc tính như quyền truy cập, ngày giờ, thư mục, và các thuộc tính khác.

3. **-z, --compress**: Sử dụng nén để giảm kích thước dữ liệu khi truyền qua mạng.

4. **-r, --recursive**: Sao chép các thư mục và tệp tin bên trong các thư mục đó.

5. **-u, --update**: Chỉ sao chép các tệp tin từ nguồn sang đích nếu tệp tin ở nguồn có nội dung mới hoặc tệp tin ở đích không tồn tại.

6. **--exclude**: Loại trừ các tệp tin hoặc thư mục cụ thể từ quá trình sao chép.

7. **--progress**: Hiển thị tiến độ của quá trình sao chép.

8. **-h, --human-readable**: Hiển thị thông tin về kích thước dữ liệu ở dạng dễ đọc cho con người.


