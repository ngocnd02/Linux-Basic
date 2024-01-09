# Redundant Array of Independent Disks (RAID)
**RAID** là một phương pháp kết hợp nhiều ổ đĩa cứng để tạo thành một hệ thống lưu trữ dữ liệu. Mục tiêu của RAID là cung cấp tính sẵn sàng và tăng cường hiệu suất hoặc độ an toàn của dữ liệu thông qua việc phân chia, sao chép hoặc mã hóa dữ liệu qua nhiều ổ đĩa.

**Mục tiêu của RAID**
- Tăng Tốc Độ và Hiệu Suất: Bằng cách chia nhỏ dữ liệu và phân phối chúng qua nhiều ổ đĩa, RAID có thể tăng tốc độ đọc và ghi dữ liệu.
- Bảo Vệ Dữ Liệu: RAID cung cấp cơ chế dự phòng để đảm bảo dữ liệu không bị mất trong trường hợp một hoặc nhiều ổ đĩa gặp sự cố.
Tăng Khả Năng Tolerant Fault: Có khả năng tiếp tục hoạt động bình thường khi một hoặc nhiều ổ đĩa gặp sự cố.

**Một số cấu hình RAID phổ biến**
1. **RAID 0 (Striping)**: Phân chia dữ liệu thành các khối nhỏ và ghi lần lượt lên các ổ đĩa. Tăng tốc độ đọc/ghi vì dữ liệu được phân tán trên nhiều ổ đĩa, nhưng không có tính dự phòng. Nếu một ổ đĩa hỏng, toàn bộ dữ liệu trong hệ thống RAID 0 có thể bị mất.
2. **RAID 1 (Mirroring)**: Tạo bản sao chép (mirror) của dữ liệu trên một hoặc nhiều ổ đĩa. Tính dự phòng cao, dữ liệu vẫn tồn tại nếu một ổ đĩa hỏng, nhưng chi phí lưu trữ sẽ tăng do cần nhiều ổ đĩa hơn.
3. **RAID 5**: Phân chia dữ liệu thành các khối và lưu trữ thông tin kiểm tra dư thừa (parity) trên các ổ đĩa khác nhau. Tính dự phòng cho phép khôi phục dữ liệu khi một ổ đĩa hỏng, nhưng hiệu suất có thể giảm trong quá trình ghi dữ liệu.
4. **RAID 6**: Tương tự như RAID 5, nhưng lưu trữ hai thông tin kiểm tra dư thừa. Cung cấp dự phòng mạnh mẽ hơn khi có nhiều ổ đĩa hỏng cùng một lúc.
5. **RAID 10 (RAID 1+0)**: Kết hợp RAID 1 và RAID 0. Dữ liệu được sao chép (mirrored) trước khi phân chia và ghi lên các ổ đĩa khác nhau, cung cấp cả dự phòng cao và hiệu suất tốt.