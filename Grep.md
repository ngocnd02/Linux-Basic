# Tìm kiếm bằng grep
Lệnh `grep` trong hệ điều hành Unix/Linux được sử dụng để tìm kiếm các dòng trong tệp tin có chứa các mẫu (patterns) phù hợp với mẫu cụ thể mà bạn định chỉ định.

- Câu lệnh: `# grep [tùy chọn] [mẫu] [tệp...]`
- Trong đó: 
	- **[tùy chọn]**: Là các cờ hoặc tùy chọn để tùy chỉnh việc tìm kiếm, ví dụ -i để tìm kiếm không phân biệt chữ hoa, chữ thường.
	- **[mẫu]**: Là chuỗi hoặc biểu thức chính quy mà bạn muốn tìm kiếm trong tệp tin.
	- **[tệp...]**: Là danh sách các tệp tin hoặc đường dẫn mà bạn muốn tìm kiếm.

- Các tùy chọn phổ biến: 

	- -i: Không phân biệt chữ hoa, chữ thường khi tìm kiếm.
	- -r hoặc --recursive: Tìm kiếm đệ quy trong tất cả các thư mục con.
	- -v hoặc --invert-match: Hiển thị các dòng không chứa mẫu tìm kiếm.
	- -n hoặc --line-number: Hiển thị số dòng của kết quả tìm kiếm.
	- -l hoặc --files-with-matches: Chỉ hiển thị tên tệp tin chứa mẫu tìm kiếm.
	- -E hoặc --extended-regexp: Sử dụng biểu thức chính quy mở rộng (Extended Regular Expressions).
	- -f file hoặc --file=file: Đọc các mẫu tìm kiếm từ tệp tin được chỉ định.
	- -w hoặc --word-regexp: Tìm kiếm chỉ các từ nguyên (whole words) thay vì chuỗi con.
	- -A num hoặc --after-context=num: Hiển thị num dòng văn bản sau mỗi kết quả tìm kiếm.
	- -B num hoặc --before-context=num: Hiển thị num dòng văn bản trước mỗi kết quả tìm kiếm.
	- -C num hoặc --context=num: Hiển thị num dòng văn bản trước và sau mỗi kết quả tìm kiếm.

- Các ví dụ:
	- grep hello file.txt: Tìm kiếm từ "hello" trong tệp tin "file.txt".
	- grep -i hello file.txt: Tìm kiếm từ "hello" mà không phân biệt chữ hoa, chữ thường trong tệp tin "file.txt".
	- grep "error message" *.log: Tìm kiếm chuỗi "error message" trong tất cả các tệp có đuôi là .log trong thư mục hiện tại.

- Cách sử dụng khác:
	- Câu lệnh: `# cat intro.txt | grep -F Michale
	- Hoặc: `# dmesg | grep -n enabled

STDIN, STDOUT, STDERR
**3 lệnh sau có ý nghĩa như nhau:**
- `# grep text file.txt`
- `# cat file.txt | grep text`
- `# grep text < file.txt`

**Những ví dụ khác**
- `# ls > result.txt` ls thư mục hiện tại và ghi kết quả vào file result.txt
- `# ls ff 2> result.txt` vì đây là 1 câu lệnh không đúng lên sẽ ghi kết quả báo lỗi vào file result.txt
