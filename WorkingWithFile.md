# Thao tác trên tập tin
## Liệt kê nội dung các thư mục
- Lệnh **ls** trong Unix/Linux được sử dụng để liệt kê nội dung của thư mục hiện tại hoặc một thư mục cụ thể. Dưới đây là một số tùy chọn phổ biến đi kèm với ls:
1. **-l**: Hiển thị danh sách các tệp tin và thư mục dưới dạng danh sách chi tiết, bao gồm thông tin về quyền truy cập, chủ sở hữu, nhóm, kích thước, thời gian sửa đổi và tên tệp tin.

Câu lệnh: `# ls -l`

![Imgur](https://i.imgur.com/tiJUuT1.png)

2. **-a**: Hiển thị tất cả các tệp tin, bao gồm cả các tệp tin ẩn (bắt đầu bằng dấu chấm).

Câu lệnh: `# ls -a`

![Imgur](https://i.imgur.com/x2cRY7l.png)

3. **-h**: Hiển thị kích thước của các tệp tin và thư mục dưới dạng dễ đọc, như "K", "M" cho kilobyte và megabyte.

Câu lệnh: `# ls -h`

4. **-t**: Sắp xếp các tệp tin theo thời gian sửa đổi, hiển thị tệp mới nhất trước.

Câu lệnh: `#ls -t`

5. **-R**: Hiển thị cả nội dung của các thư mục con (đệ quy).

Câu lệnh: `#ls -R`

![Imgur](https://i.imgur.com/Ei1uqEH.png)

## Chuyển thư mục
- **cd /duong/dan/tuyet/doi** : chuyển tới thư mục /doi/
- **cd** : chuyển về thư mục chính của người dùng
- **cd A && ls** : chuyển tới thư mục A và hiện danh sách các file của nó.

![Imgur](https://i.imgur.com/kuci6mS.png)

- **cd -**: chuyển về thư mục đang làm việc trước đó.
- **cd ..** : chuyển về thư mục cha.
- **cd /**: Chuyển đến thư mục gốc (root directory) của hệ thống tệp.

## Tạo thư mục
- Để tạo một thư mục mới trong dòng lệnh có thể sử dụng lệnh mkdir (make directory). 
	- Câu lệnh: `# mkdir <tên_folder>`
- Nếu bạn muốn tạo một thư mục con bên trong thư mục hiện tại, bạn có thể chỉ định đường dẫn tương đối hoặc tuyệt đối

![Imgur](https://i.imgur.com/N4lEvZy.png)

- Nếu bạn muốn tạo nhiều thư mục cùng một lúc, chỉ cần liệt kê chúng sau lệnh mkdir:
	- Câu lệnh: `mkdir folder1 folder2 folder3`

- Các tùy chọn phổ biến: 
1. **-p**: Tạo các thư mục cha nếu chúng chưa tồn tại. Điều này hữu ích khi bạn muốn tạo một thư mục con nhưng thư mục cha của nó chưa tồn tại.
Ví dụ: `# mkdir mkdir -p parent_folder/child_folder/grandchild_folder` sẽ tạo parent_folder, child_folder trong parent_folder, và grandchild_folder trong child_folder nếu chúng không tồn tại.

![Imgur](https://i.imgur.com/G9oF6Kj.png)

2. **-m**: Đặt quyền truy cập cho thư mục được tạo mới.
Ví dụ: `# mkdir -m 775 new_folder`

## Tạo tệp tin 
Để tạo một tệp tin mới trong dòng lệnh Unix/Linux, bạn có thể sử dụng một số lệnh như **touch**, **echo** kết hợp với redirection hoặc **cat** . Dưới đây là một số cách để tạo một tệp tin mới:
- Sử dụng lệnh **touch**:
	- Câu lệnh: `# touch new_file.txt`

- Sử dụng lệnh **cat** kết hợp với **redirection >**:
	- Câu lệnh: `# cat > filename.txt`
Nhập nội dung cho tệp tin và ấn **Ctrl + D** khi hoàn thành việc nhập để lưu tệp

- Sử dụng lệnh **echo** kết hợp với **redirection >**:
	- Câu lệnh: `# echo "Hello, world!" > filename.txt`
Lệnh trên sẽ tạo một tệp tin có tên filename.txt và ghi nội dung "Hello, world!" vào tệp.

- Các tùy chọn hay sử dụng cùng lệnh touch: 
1. **-c**: Nếu tệp tin không tồn tại, không tạo tệp mới. Không thông báo lỗi.
	- Câu lệnh: `# touch -c filename.txt`

2. **-m**: Chỉ cập nhật thời gian sửa đổi của tệp tin, không tạo tệp mới nếu tệp chưa tồn tại.
	- Câu lệnh: `# touch -m filename.txt`
3. **-a**: Chỉ cập nhật thời gian truy cập của tệp tin, không tạo tệp mới nếu tệp chưa tồn tại.
	- Câu lệnh: `# touch -a filename.txt`
4. **touch -d** trong Linux được sử dụng để đặt thời gian truy cập và sửa đổi của một tệp tin hoặc nó có thể được sử dụng để tạo một tệp tin mới với thời gian xác định.
	- Câu lệnh: `# touch -d "2023-01-01 08:00:00" myfile.txt`

## Lệnh xóa tập tin
- Để xóa một tập tin trong Linux, có thể sử dụng lệnh **rm** (remove)
	- Câu lệnh: `# rm filename.txt`

- Nếu bạn muốn xóa nhiều tập tin cùng một lúc, bạn có thể liệt kê chúng:
	- Câu lệnh: rm file1 file2 file3

![Imgur](https://i.imgur.com/FsRo30Q.png)

- Các tùy chọn có thể dùng cùng lệnh **rm**

1. **-f**: `Xóa tập tin` mà không yêu cầu xác nhận từ người dùng. Thường được sử dụng để gỡ bỏ các tệp không thể xóa bình thường hoặc để xóa nhanh chóng mà không cần xác nhận.
	- Câu lệnh: `rm -f filename.txt`
2. **-i**: Yêu cầu xác nhận từ người dùng trước khi xóa mỗi tập tin
	- Câu lệnh: `rm -i filename.txt`

## Lệnh xóa thư mục:
- Để xóa một thư mục ta sử dụng **rmdir**
	- Câu lệnh: `# rmdir my_folder`
Tuy nhiên lệnh này chỉ có thể xóa được những thư mục rỗng. Nếu thư mục chứa các thư mục con lệnh này sẽ không hoạt động

1. **-r, -R** : `Xóa thư mục` và nội dung bên trong nó một cách đệ quy (recursive).
	- Câu lệnh: `# rm -r parent_folder`

![Imgur](https://i.imgur.com/dFc7Us9.png)

2. Nếu muốn xóa nhanh một thư mục mà k cần xác nhận xóa từng thư mục một, ta kết hợp `rm -rf`
	- Câu lệnh: `# rm -rf parent_folder`

![Imgur](https://i.imgur.com/oXV8afv.png)

## Mở tập tin
Để có thể mở các tập tin ta có thể dùng các lệnh sau: 
- Sử dụng lệnh **cat**, nó sẽ hiển thị nội dung trên terminal
	- Câu lệnh:`# cat filename.txt`

![Imgur](https://i.imgur.com/LMri9Hs.png)

Các tùy chọn đi cùng phổ biến với lệnh **cat**
1. **-n**: Hiển thị số dòng trên mỗi dòng.
	- Câu lệnh: `# cat -n filename.txt`

![Imgur](https://i.imgur.com/AAOuypB.png)

2. **-E**: Hiển thị ký tự dấu $ ở cuối mỗi dòng.
	- Câu lệnh: `# cat -E filename.txt`

3. **-A**: Hiển thị tất cả các ký tự điều khiển, bao gồm cả tab và dấu xuống dòng.

	- Câu lệnh: `# cat -A filename.txt`
4. **-b** Hiển thị số dòng cho dòng không trống .
	- Câu lệnh: `# cat -b filename.txt`

![Imgur](https://i.imgur.com/DUepji4.png)

5. **-s**: Kết hợp nhiều dòng trống thành một dòng trống.
	- Câu lệnh: `# cat -s filename.txt`

- Sử dụng lệnh **less* để xem tập tin theo trang về có thể di chuyển qua lại dễ dàng 
	- Câu lệnh: `# less filename.txt`

![Imgur](https://i.imgur.com/HNCfX2v.png)

Cách sử dụng trong **less**:
	- Dùng mũi tên lên xuống để đọc file
	- Muốn di chuyển đến cuối văn bản: **shift g**
	- Muốn chuyển đến đầu văn bản: **g**
	- Nhấn q để thoát 
	- Tìm kiếm: Nhấn **/** và gõ kí tự muốn tìm kiếm, sử dụng **n** để di chuyển đến lần xuất hiện tiếp theo, và **N** để xuất hiện đến lần trước đó. Nếu bạn muốn tìm kiếm từ cuối file lên đầu, bạn có thể sử dụng dấu **?** thay vì **/**, sau đó thực hiện tìm kiếm như thông thường.

Các tùy chọn trong lệnh less:
1. **less filename**: Mở tệp tin để xem nội dung.
2. **less +F filename**: Mở tệp và chuyển sang chế độ theo dõi (tương tự tail -f), đọc tệp tin khi có thêm dữ liệu được thêm vào.
3. **less -N filename**: Hiển thị số dòng trên mỗi dòng.
4. **less -S filename**: Ngăn không cho các dòng quá dài tự động quấn xuống dòng mới.
5. **less -X filename**: Tắt chế độ phím tắt.

- Sử dụng lệnh **more** để xem tập tin 
	- Câu lệnh: `# more filename.txt`

- Sử dụng lệnh **head** để hiện thị phần đầu của tập tin
	- Câu lệnh: `# head filename.txt`
Mặc định lệnh **head** sẽ hiển thị 10 dòng đầu tiên của file, bạn cũng có thể chỉ định số lượng dòng bằng tùy chọn **n**
	- Câu lệnh: `# head -n 15 filename.txt`

- Sử dụng lệnh **tail** để hiện thị phần cuối của tập tin
	- Câu lệnh: `# tail filename.txt`
Mặc định lệnh **tail** sẽ hiển thị 10 dòng cuối cùng.

Cả head và tail cũng có khả năng theo dõi dữ liệu đến khi có thêm thông tin được thêm vào tệp tin bằng cách sử dụng tùy chọn -f (theo dõi, tương tự như tail -f)
	- Câu lệnh: `# tail -f filename.txt`

- Ngoài ra chúng ta có thể sử dụng các trình soạn thảo như ** vi** để đọc dữ liệu. 

## Trình soạn thảo vi
Trình soạn thảo vi là một công cụ mạnh mẽ trong linux. Vi có 2 chế độ làm việc chính 
- 1. **Command Mode (Chế độ lệnh)**: Đây là chế độ mặc định khi bạn mở vi. Trong chế độ này, bạn có thể di chuyển trong file, xóa, sao chép, dán và thực hiện các thao tác chỉnh sửa khác. Bạn cũng có thể chuyển sang chế độ Insert Mode để nhập văn bản mới.
- 2. **Insert Mode (Chế độ chèn)**: Chế độ này cho phép bạn nhập văn bản vào file. Trong chế độ này, bạn có thể nhập và chỉnh sửa văn bản theo cách thức thông thường như các trình soạn thảo văn bản khác.

Để chuyển giữa hai chế độ này:

- **Từ Command Mode sang Insert Mode**: Nhấn phím i để bắt đầu nhập văn bản từ vị trí con trỏ hiện tại.
- **Từ Insert Mode sang Command Mode**: Khi bạn đã hoàn thành việc nhập văn bản, nhấn Esc để trở lại Command Mode.

Cách sử dụng vi
- Câu lệnh: `# vi <tên_file>`, nếu file chưa tồn tại vi sẽ tạo ra một file mới, nếu file đã tồn tại vi sẽ mở file trong trang làm việc
- Trong trình soạn thảo vi ta có thể dùng mũi tên lên xuống để di chuyển giữa các dòng. 
- Nếu ta muốn **copy** bất kì dòng nào, ta di chuyển con trỏ đến dòng đó, sau đó gõ **yy** để copy. Sau đó ta di chuyển con trỏ đến dòng muốn copy, sau đó nhấp **p** để paste.
- Muốn **xóa** một dòng văn bản trong vi, di chuyển trỏ chuyện đến dòng muốn xóa và gõ **dd**. Giả sử sau khi khóa xong ta muốn khôi phục thì ta gõ chữ *u* (undo) để khôi phục.
- Khi chúng ta muốn **tìm kiếm** trên văn bản, gõ kí tự / sau đó gõ kí tự muốn tìm, muốn đi đến kết quả tiếp theo ta gõ chữ n (next).
- Khi chúng ta muốn **thay thế từ** trong văn bản ta gõ `% s/[từ muốn thay thế]/[từ mới để thay thế]/g`. VD: %s/day/thu/g.
- Muốn xem **số thứ tự** dòng văn bản trên vi, gõ : **set nu** ( nu là number), nếu muốn bỏ đánh số thứ tự thì gõ:  **set nonu**

- Để lưu tệp tin và thoát "vi," bạn nhấn phím `Esc` để chắc chắn bạn đang ở chế độ Command Mode. Sau đó, gõ `:wq` và nhấn Enter. "wq" có nghĩa là "write" (lưu) và "quit" (thoát). Nếu bạn chỉ muốn lưu mà không thoát, bạn có thể gõ `:w` và nhấn Enter.
- Để thoát "vi" mà không lưu thay đổi, bạn nhấn phím `Esc` để đảm bảo bạn ở chế độ Command Mode, sau đó gõ `:q!` và nhấn Enter. "q!" có nghĩa là "quit" (thoát) và "force" (buộc thoát).

## Copy file
1. **Sao chép file**
- Câu lệnh: `# cp nguồn đích `

![Imgur](https://i.imgur.com/rOil4xT.png)

2. **Sao chép nhiều file vào một thư mục**
- Câu lệnh: `# cp file1.txt file2.txt /đường/dẫn/mục/đích`

![Imgur](https://i.imgur.com/5nZzBw9.png)

3. **Sao chép thư mục và nội dung bên trong**
- Câu lệnh : `cp -r thư_mục_nguồn /đường/dẫn/mục/đích`
- *Lưu ý*: Tùy chọn -r (hoặc --recursive) là cần thiết khi bạn muốn sao chép toàn bộ cây thư mục và nội dung bên trong.

![Imgur](https://i.imgur.com/fARDdIe.png)

- *Các tùy chọn phổ biến của lệnh `cp`*
1. **-r (hoặc --recursive)**: Được sử dụng để sao chép thư mục và nội dung bên trong của nó. Nếu bạn muốn sao chép toàn bộ cây thư mục, tùy chọn này là cần thiết.

Ví dụ: cp -r /nguồn /đích

2. **-i (hoặc --interactive)**: Yêu cầu xác nhận trước khi ghi đè lên file đích nếu file đích đã tồn tại.

Ví dụ: cp -i file1.txt /đích

![Imgur](https://i.imgur.com/7SthuO4.png)

3. -v (hoặc --verbose): Hiển thị thông báo chi tiết về quá trình sao chép, bao gồm tên của file hoặc thư mục được sao chép.

Ví dụ: cp -v file1.txt /đích

![Imgur](https://i.imgur.com/72hxlsx.png)

4. **-u (hoặc --update)**: Chỉ sao chép file nếu file nguồn mới hơn hoặc không tồn tại trong thư mục đích.

Ví dụ: cp -u file1.txt /đích

5. **-n (hoặc --no-clobber)**: Không ghi đè lên file đích nếu file đích đã tồn tại.

Ví dụ: cp -n file1.txt /đích

6. **-p (hoặc --preserve)**: Giữ nguyên các thuộc tính của file gốc như thời gian sửa đổi, quyền truy cập, ...

Ví dụ: cp -p file1.txt /đích

7. **-a (hoặc --archive)**: Kết hợp các tùy chọn -d, -r, và -p để sao chép các file và thư mục với tất cả các thuộc tính và đệ quy.

Ví dụ: cp -a /nguồn /đích

## So sánh các file
Lệnh **diff** trong Linux được sử dụng để so sánh và tìm ra sự khác biệt giữa hai tập tin hoặc thư mục. Đây là một số cách sử dụng thông dụng của lệnh diff:
1. **So sánh 2 file**:
- Câu lệnh: `# diff file1.txt file2.txt`
- Lệnh này sẽ so sánh hai file file1.txt và file2.txt và hiển thị các dòng có sự khác biệt giữa chúng.

![Imgur](https://i.imgur.com/RwDOm0h.png) 

2. **So sánh nội dung giữa thư mục**
- Câu lệnh: `# diff -r thư_mục_1 thư_mục_2`
- Tùy chọn -r hoặc --recursive sẽ cho phép so sánh đệ quy giữa hai thư mục thư_mục_1 và thư_mục_2. Lệnh này sẽ hiển thị các file hoặc thư mục khác nhau trong cả hai thư mục.

![Imgur](https://i.imgur.com/Pk1D2Nv.png)

3. **Ghi kết quả vào file**
- Câu lệnh: `# diff file1.txt file2.txt > ketqua.diff`
- Dùng dấu > để chuyển kết quả so sánh vào một file mới, ở đây là ketqua.diff.

![Imgur](https://i.imgur.com/W3DoogG.png)

4. **Xem chỉ những dòng khác biệt**
- Câu lệnh: `# diff -u file1.txt file2.txt`
- Tùy chọn -u (hoặc --unified) hiển thị kết quả với định dạng thống nhất và dễ đọc hơn, với thông tin chi tiết về những thay đổi.

5. **Xem thông tin chi tiết về các dòng cụ thể**
- Câu lệnh: `# diff -c file1.txt file2.txt`
- Tùy chọn -c (hoặc --context) cung cấp thông tin chi tiết hơn về những sự khác biệt, bao gồm cả các dòng xung quanh để giúp bạn dễ hiểu hơn về ngữ cảnh của sự thay đổi.

## Xác định kiểu file
-  xác định kiểu file trong Linux, bạn có thể sử dụng lệnh **file**. Lệnh này sẽ cho bạn thông tin về loại file dựa trên nội dung và cấu trúc của file đó

1. **Xác định kiểu file cụ thể**
- Câu lệnh: `# file <tên file>`
2. **Xác định kiểu nhiều file cùng lúc**
- Câu lệnh: `# file file1.txt file2.jpg file3.pdf`

## Nén và giải nén 
Trong Linux, để nén và giải nén các file hoặc thư mục, có thể sử dụng các công cụ như tar, gzip, bzip2, zip, và unzip. Dưới đây là một số cách thực hiện nén và giải nén:
#### Sử dụng tar
Nén 
- Câu lệnh: `# tar -czvf ten_file.tar.gz /duong/dan/thu_muc_hoac_file`
- Lệnh tar sẽ nén toàn bộ nội dung từ thư mục được chỉ định và tạo thành thư mục có tên được đặt với đuôi .tar.gz
Trong đó: 
	- **-c**: Tạo file tar mới.
	- **-z**: Sử dụng gzip để nén.
	- **-v**: Hiển thị thông tin chi tiết khi nén.
	- **-f**: Xác định tên file đầu ra.

![Imgur](https://i.imgur.com/xWCKWRB.png)

- Nén nhiều file hoặc thư mục
	- Câu lệnh: `# tar -czvf ten_file.tar.gz file1 file2 folder1 folder2`
	- Lệnh này sẽ nén file1, file2, folder1, folder2 vào ten_file.tar.gz

![Imgur](https://i.imgur.com/xun7Qp2.png)

- Xem nội dung file nén
	- Câu lệnh: `# tar tar -tzvf filenen.gz.tar | more`
	- **-t** cho biết đang muốn xem nội dung file nén 

![Imgur](https://i.imgur.com/mHGlTwx.png)

Giải nén
- Câu lệnh: `tar -xzvf ten_file.tar.gz`
Trong đó: 
	- **-x**: Giải nén file tar.
	- **-z**: Sử dụng gzip để giải nén.
	- **-v**: Hiển thị thông tin chi tiết khi giải nén.
	- **-f**: Xác định file đầu vào.

#### Sử dụng gzip
Nén
- Câu lệnh: `# gzip ten_file`
- Sẽ tạo ra file nén `ten_file.gz`

![Imgur](https://i.imgur.com/aEDpXt8.png)

- Các tùy chọn phổ biến: 
1. **-f, --force**: Nén mạnh mẽ, ghi đè lên file nén nếu đã tồn tại
Câu lệnh: gzip -f ten_file

2. **-k, --keep**: Giữ file gốc sau khi nén, không xóa file gốc.
Câu lệnh: gzip -k ten_file

3. **gzip -9 ten_file**
Điều chỉnh mức độ nén từ 1-9 (1: nén ít, 9 nén mạnh). Mặc định là 6

Giải nén
- Câu lệnh: `# gzip -d ten_file.gz`


#### Sử dụng bzip2
Nén
- Câu lệnh: `# bzip2 ten_file`
- Sẽ tạo ra file nén `ten_file.bz2`

Kết hợp với tar
- Câu lệnh: `# tar -cjvf ten_file.tar.bz2 /duong/dan/thu_muc_hoac_file`
- Trong đó **-j** là tham số để sử dụng bzip2 để nén file.

Giải nén
- Câu lệnh: `# bzip2 -d ten_file.bz2`

Kết hợp với tar
- Câu lệnh: `# tar -xjvf ten_file.tar.bz2`

#### Sử dụng zip
Nén
- Câu lệnh: `# zip ten_file.zip /duong/dan/thu_muc_hoac_file`

Giải nén
- Câu lệnh: `# unzip ten_file.zip`

