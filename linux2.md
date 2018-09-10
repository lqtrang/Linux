### Thư mục home
Trong bất cứ hệ thống Linux nào, mỗi người dùng đều có thư mục home riêng của họ, thường nằm sau `/home`. Thư mục `/home` thường được mount như là một hệ thống tập tin riêng biệt trên phân vùng riêng của nó hoặc xuất phát từ một mạng thông qua NFS.

### Thư mục binary
Thư mục `/bin` chứa các tệp nhị phân thực thi, các lệnh cần thiết sử dụng trong chế độ một ngừoi dùng, ví dụ: ps, ls, cp..Các lệnh không cần thiết cho hệ thống ở chế độ một ngừoi dùng thì được đặt trong thư mục `/usr/bin`, trong khi thư mục `/sbin` được sử dụng cho các tệp nhị phân cần thiết liên quan đên quản trị hệ thống, vd như `ifconfig` và `shutdown`. Cũng có một thư mục `/usr/sbin` cho các chương trình quản trị hệ thống ít cần thiết hơn.Tất cả các thư mục nhị phân đều nằm trong phân vùng gốc. Đôi khi `/ usr` là một hệ thống tệp riêng biệt có thể không khả dụng ở chế độ một người dùng. Đây là lý do tại sao các lệnh cần thiết được tách ra khỏi các lệnh không cần thiết. Tuy nhiên, trong một số hệ thống Linux hiện đại nhất thì sự phân biệt này được xem là lỗi thời, `/usr/bin` và `/bin` thực sự chỉ được liên kết với nhau như `/usr/sbin` và `/sbin`.

### Thư mục device
Thư mục `/dev` chứa các nút thiết bị, một loại file ảo được hầu hết các thiết bị phần cứng và phần mềm sử dụng, ngoại trừ thiết bị mạng. Thư mục này rỗng trong phân vùng đĩa khi nó không được mount, nhưng nó chứa các thư mục được tạo bởi hệ thống `udev`, thứ mà tạo và quản lý các nút thiết bị trong Linux, tạo ra một cách linh động khi tìm thấy thiết bị.

### Thư mục variable
Thư mục `/var` chứa các file được dự kiến sẽ thay đổi về kích thước và nội dung khi hệ thống đang chạy. Ví dụ như:
<ul>
    <li>File log: `/var/log`</li>
    <li>Packages files: `/var/lib`</li>
    <li>Temp files: `/var/tmp`</li>
</ul>
Thư mục `/var` có thể được đặt trong phân vùng riêng để sự thay đổi về kích thước của tệp tin có thể được cung cấp mà không làm ảnh hưởng đến hệ thống.

### Thư mục cấu hình hệ thống
Thư mục `/etc` là trang chủ của các file cấu hình hệ thống. Nó không chứa các chương trình nhị phân, mặc dù có một số tập lệnh thực thi. Ví dụ: Tệp `resolv.conf` chỉ cho hệ thống cách có được host name để ánh xạ địa chỉ IP(DNS). Các tệp như `passwd`, `shadow` và `group` để quản lý tài khoản người dùng được tìm thấy trong thư mục `/ etc`. 

### Thư mục boot
Thư mục `/boot` chứa một số tệp cần thiết để khởi động hệ thống. Với mỗi nhân thay thế được cài đặt trên hệ thống có bốn file:
<ul>
    <li>`vmlinuz` là nhân linux được nén, cần thiết để khởi động </li>
    <li>`initramfs` hệ thống tập tin ram ban đầu, cần thiết để khởi động</li>
    <li>`config is` Tệp cấu hình nhân, chỉ sử dụng để gỡ lỗi</li>
    <li>`System.map` Chứa bảng ký hiệu nhân, chỉ sử dụng để gỡ lỗi</li>
</ul>

### Thư mục libbraries
Thư mục `/lib` chứa các  thư viện cho các chương trình thiết yếu trong thư mục `/bin` và `/sbin`.Phần lớn trong số này được biết đến như là thư viện được nạp tự động. Trên một số bản Linux tồn tại thư mục `/lib64` chứa thư viện 64 bit trong khi `/lib` chứa các phiên bản 32 bit.Các module hạt nhân được đặt lại tại `/lib/modules/`.

### Thư mục Additional
| Danh mục| Cách sử dụng |
|---------|-------|
| /opt | Các gói phần mềm ứng dụng tùy chọn |
| /sys | Hệ thống file ảo  cung cấp thông tin về hệ thống và phần cứng. Có thể được sử dụng để thay đổi các tham số hệ thống và cho các mục đích gỡ lỗi. | 
| /srv | Dữ liệu trang web cụ thể được hệ thống phân phối. Ít khi sử dụng. |
| /tmp | Hồ sơ tạm thời |
| /media | Thường đặt ở nơi các thiết bị di động, chẳng hạn như đĩa CD, DVD và ổ USB được lắp. Trừ khi cấu hình không cho phép, Linux sẽ tự động mount các media trong thư mục này khi chúng được phát hiện. |
| /usr | Ứng dụng, tiện ích và dữ liệu đa người dùng |
| /usr/include | Các file tiêu đề được sử dụng để biên dịch ứng dụng |
| /usr/lib | Thư viện cho các chương trình nhị phân |
| /usr/lib64 | Thư viện 64 bit cho các chương trình nhị phân |
| /usr/share | Dữ liệu được chia sẻ được các ứng dụng sử dụng, thường độc lập về kiến ​​trúc |
| /usr/src | Mã nguồn, thường cho nhân Linux |
| /usr/local | Dữ liệu và chương trình cụ thể cho máy cục bộ |

### File System Table

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
