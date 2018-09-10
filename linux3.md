### File permissions
Trong Linux và các hệ điều hành UNIX khác, mọi tệp đều được liên kết với người dùng là chủ sở hữu.
| Command | Kết quả |
|---------|-------|
| chown | Được sử dụng để thay đổi quyền sở hữu người dùng của tệp hoặc thư mục |
| chgrp | Được sử dụng để thay đổi quyền sở hữu nhóm |
| chmod | Được sử dụng để thay đổi các quyền trên file |

Mỗi file có 3 loại quyền: read (r), write (w), execute (x). Chúng thường được thể hiện theo thứ tự sau rwx.Các quyền này ảnh hưởng đến ba nhóm chủ sở hữu: user (u), group (g), and others (o).
 
| rwx: | rwx: | rwx |
|------|------|-----|
| u: | g: | o |

Có một số cách khác nhau để sử dụng lệnh `chmod`. Ví dụ: để cho phép chủ sở hữu thực thi quyền.

### Package Management Systems
Các phần cốt lõi của bản phân phối Linux và phần lớn các phần mềm bổ sung của nó được cài đặt thông qua Hệ thống quản lý gói. Mỗi gói chứa các tệp và các hướng dẫn khác cần thiết để làm cho một thành phần phần mềm hoạt động trên hệ thống. Các gói có thể phụ thuộc vào nhau. Có hai họ quản lý gói lớn: những người dựa trên dpkg và những người sử dụng rpm để quản lý gói cấp thấp của họ. Hai hệ thống không tương thích, nhưng cung cấp các tính năng tương tự ở mức độ lớn.

| Hoạt động | RPM | Debian |
|--------------|-------|------|
| Cài đặt gói | rpm –i foo.rpm | dpkg --install foo.deb |
| Cài đặt gói có phụ thuộc từ kho lưu trữ | yum install foo | apt-get install foo |
| Xóa một gói | rpm –e foo.rpm | dpkg --remove foo.deb |
| Xóa gói và phụ thuộc bằng kho lưu trữ | yum remove foo | apt-get remove foo |
| Cập nhật gói lên phiên bản mới hơn | rpm –U foo.rpm | dpkg --install foo.deb |
| Cập nhật gói bằng kho lưu trữ và giải quyết các phụ thuộc | yum update foo | apt-get upgrade foo |
| Cập nhật toàn bộ hệ thống | yum update | apt-get dist-upgrade |
| Hiển thị tất cả các gói đã cài đặt | yum list installed | dpkg --list |
| Nhận thông tin về gói đã cài đặt bao gồm tệp | rpm –qil foo | dpkg --listfiles foo |
| Hiển thị gói có sẵn với "foo" trong tên | yum list foo | dpkg --listfiles foo |
| Hiển thị tất cả các gói có sẵn | yum list | apt-cache dumpavail |
| Hiển thị các gói mà một tệp thuộc về | rpm –qf file | dpkg --search file |

### Backup the data
Lệnh `rsync` dúng để đồng bộ hóa hoàn toàn cây thư mục. Về cơ bản, nó sao chép file giống lênh `cd`. Ngoài ra, `rsync` còn kiểm tra tệp được sao chép đã tồn tại hay chưa. Nếu file đã tồn tại và không có gì thay đổi về kích thước hay thời gian sửa đổi, `rsync` sẽ tranh được một bản sao không cần thiết và tiết kiệm thời gian.
`rsync` rất hiệu quả khi đệ qui sao chép một cây thư mục qua mạng, bởi vì chỉ có sự khác biệt mới được truyền.

### Compress the data
File dữ liệu thường được nén để tiết kiệm dung lượng đĩa và giảm thời gian cần để truyền tệp qua mạng. Linux sử dụng một số phương pháp để thực hiện công việc này:
| Lệnh | Cách sd |
|------|---------|
| gzip | Được sử dụng thường xuyên nhất |
| bzip | Tạo file nhỏ hơn đáng kể so với các file được tạo ra bở gzip |
| xz | Tiện ích nén hiệu quả nhất về không gian được sử dụng trong Linux. Nó hiện đang được sử dụng bởi kernel.org để lưu trữ nhân Linux. |
| zip | Thường được yêu cầu để kiểm tra và giải nén lưu trữ từ các hệ điều hành khác |
