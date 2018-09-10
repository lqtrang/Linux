### Lưu trữ dữ liệu
Lệnh `tar` cho phép bạn tạo hoặc trích xuất các tệp từ tệp lưu trữ, thường được gọi là tarball. Đồng thời, bạn có thể tùy chọn nén trong khi tạo lưu trữ và giải nén trong khi trích xuất nội dung của nó.
| Lệnh | Tác dụng |
|--------------|-------|
| tar xvf mydir.tar | Trích xuất tất cả các file trong mydir.tar vào thư mục mydir|
| tar zcvf mydir.tar.gz mydir | Tạo kho lưu trữ và nén bằng gzip |
| tar jcvf mydir.tar.bz2 mydir | Tạo kho lưu trữ và nén bằng bz2 |
| tar xvf mydir.tar.gz | Giải nén tất cả các file trong mydir.tar.gz vào thư mục mydir |
| tar cvf mydir.tar | Hiển thi nội dung vào thư mục mydir |

### Sao chép đĩa
Lệnh `dd` rất hữu ích để tạo bản sao của không gian đĩa.

### Bản phát hành Linux và thông tin hệ thống
Lệnh phát hành và phân phối Linux
<img src="https://imgur.com/a/ryiA63K">
Phiên bản của nhân
Thông tin bộ nhớ
Hệ thống tập tin
<img src="https://imgur.com/a/zJXXOTj">

### Hệ thống tập tin proc
Hệ thống tập tin `/proc` chứa các file ảo chỉ tồn tại trong bộ nhớ. Hệ thống tập tin này chứa các file và thư mục bắt chước cấu trúc hạt nhân và thông tin cấu hình.

### Hostname
Hostname xác định máy trong miền.
Set lại hostname :
`# hostname NEW_NAME`
Tên sau khi được set lại sẽ vẫn giữ nguyên cho đến khi khửoi động lại hện thống. Đối vứoi hệ thống dựa tren Debian, sử dụng file `/etc/hostname` để đọc hostname của hệ thống trong thời gian khởi độnG VÀ thiết lập nó bằng một đoạn mã khởi tạo `/etc/init.d/hostname.sh`. Hostname được lưu bởi `/etc/hostname`sẽ được giữ nguyên khi khởi động lại hệ thống và sẽ được cài đặt bằng cùng một tập lệnh mà chúng ta đã sử dụng. 
Đối với hệ thống dựa trên RedHat, ta sử dụng `hostnamectl`.

### Linux swap memory
Linux chia RAM thành các vùng nhớ được gọi là các trang.
Swap (hoán đổi) là một vùng trên ổ đĩa mà nó có thể được sử dụng để lưu trữ các dữ liệu mà không được sử dụng trên bộ nhớ vật lý (RAM). Đây là nơi tạm thời chứa các tài nguyên đang không hoạt động trong bộ nhớ.

Swap được sử dụng khi hệ thống của bạn quyết định rằng nó cần thêm bộ nhớ RAM cho quá trình hoạt động và bộ nhớ RAM không còn dư để sử dụng. Nếu điều đó xãy ra, các tài nguyên và dữ liệu tạm thời không hoạt động trên bộ nhớ RAM sẽ được di chuyển để lưu trữ vào không gian Swap để giải phóng bộ nhớ RAM và sử dụng cho việc khác.
Swap cần thiết khi:
<ul>
    <li>
        Chế độ ngủ đông (Hibernation) – Trong Ubuntu, nếu bạn muốn sử dụng tính năng ngủ đông (suspend-to-disk) thì bạn cần phải có phân vùng Swap.
    </li>
    <li>
        Tối ưu hóa bộ nhớ – Hệ thống sẽ di chuyển các tài nguyên và dữ liệu hiện không được sử dụng trong bộ nhớ RAM đến Swap, điều này giúp hệ thống phục vụ cho các mục đích khác tốt hơn.
    </li>
     <li>
        Tránh các trường hợp không lường trước – Trong một số trường hợp, bạn không dự tính được bộ nhớ dành cho các chương trình mà bạn chuẩn bị thử nghiệm hoặc bất cứ điều gì đó bất thường. Trong trường hợp này, Swap sẽ được sử dụng để hệ thống có thể được duy trì để tiếp tục chạy (mặc dù nó là chậm) thay vì hệ thống đột ngột dừng lại vì thiếu bộ nhớ.
    </li>    

</ul>

Tạo file swap
`sudo fallocate -l 512m /swapfile`
Lệnh trên sẽ tạo ra file swapfile có kích thước 512MB tại /

Sau khi đã có một file swap, có thể kiểm tra bằng lệnh
`sudo swapon -s`
