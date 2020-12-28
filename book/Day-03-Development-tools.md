# **Development tools**

1. [GIT](#1-git)
2. [MySQL](#2-mysql)
3. [Apache](#3-apache)
4. [OpenServer](#4-openserver)
5. [PhpStorm](#5-phpstorm)
6. [Chrome dev tool](#6-chrome-dev-tool)

##1. GIT

Git is a distributed version control system

**VCS(Version Control System)**

    - 
    
- Git lưu trữ thông tin dưới dạng danh sách các thay đổi dựa trên file và những thay đổi được thực hiện đối với 
mỗi file theo thời gian.

- Trong các dự án thường có rất nhiều các lập trình viên làm việc song song nên Git là rất cần thiết để đảm bảo 
không có xung đột code giữa các lập trình viên.

- 1 số lợi ích của Git:
     - Dễ sự dụng, thao tác nhanh gọn, lẹ và an toàn.
     - Dễ dàng kết hợp các phân nhánh (branch).
     - chỉ cần clone mã nguồn từ kho chứa hoặc clone 1 phiên bản thay đổi nào đó từ kho chứa, hoặc 1 nhánh nào đó
     từ kho chứa là bạn có thể làm việc mọi lúc mọi nơi.
     - Deployment sản phẩm của bạn dễ dàng.

- 1 số thuật ngữ Git quan trọng:

1. Branch
- Các Branch(nhánh) đại diện cho các Phiên bản cụ thể của 1 kho lưu trữ tách ra từ Project chính của bạn.
- Branch cho phép bạn theo dõi các thay đổi của bạn đối với kho lưu trữ, bạn có thể quay về lại các phiên bản cũ hơn.

2. Commit
- Commit đại diện cho 1 thời điểm cụ thể trong lịch sử dự án của bạn. Sử dụng lệnh commit và git add giúp cho những 
thay đổi của bạn được lưu vào local repository.

3. Checkout
- Sử dụng git checkout để chuyển giữa các Branch
    - git checkout "name-branch"
 
4. Fetch
- Lệnh git fetch tìm nạp các bản sao và tải xuống tất cả các Branch vào máy tính của bạn

5. Head
- Các commit ở đầu của 1 branch được gọi là Head, Nó đại diện cho commit mới nhất của repository mà bạn đang làm việc.

6.  Index
- Bất cứ khi nào bạn thêm, sửa, xóa hoặc thay đổi file, nó vẫn nằm trong chỉ mục cho đến khi bạn sẵn sàng commit.
Sử dụng git status để xem các thay đổi đó (file index).

7. Master
- Master là nhánh chính của repository của bạn. Nó bao gồm những thay đổi và commit gần đây nhất.

8. Merge
- lệnh git merge kết hợp với các yêu cầu kéo (pull requests) để thêm các thay đổi từ nhánh này sang nhánh khác.

9. Origin
- git push origin master => để đẩy các thay đổi cục bộ đến nhánh chính.

10. Pull
- Để kéo hết code đã được push về nhánh của bạn
    - git pull

11. Push
- lệnh git push được sử dụng để đẩy code lên nhánh của bạn.

12. Rebase
- Lệnh git rebase cho phép bạn phân tách, di chuyển, thoát commit . Nó cũng có thể được sử dụng để kết hợp 2 nhánh lại 
với nhau.

13. Stash
- Lệnh git stash để lưu lại các công việc mình đang làm việc trên branch hiện tại, dùng git stash apply để quay trở lại 
thời điểm chưa git stash. 


##2. MySQL
- MySql là một hệ thống quản trị cơ sở dữ liệu mã nguồn mở.
- 1 số công cụ miễn phí dùng làm MySql:
    - MySql Workbench (Mac, Windows, Linux), miễn phí, mã nguồn mở.
    - Sequel Pro (Mac), miễn phí, mã nguồn mở.
    - HeidiSQL (Windows), miễn phí.
    - PhpMyAdmin (web app), miễn phí, mã nguồn mở.
    
- Cách hoạt động của MySql
    - MySql tạo ra bảng để lưu trữ dữ liệu, định nghĩa sự liên quan giữa các bảng đó.
    - Client sẽ gửi yêu cầu SQL bằng một mệnh lệnh đặc biệt trên MySql.
    - Ứng dụng trên server sẽ phản hồi thông tin và trả về kết quả trên máy client.
    
##3. Apache
- Apache (Apache HTTP Server) là 1 Chương trình máy chủ giao tiếp bằng giao thức HTTP và hoạt động trên hầu hết các hệ 
điều hành như: Linux, Windows, Unix và nhiều hệ điều hành khác.

- Apache đóng vai trò quan trọng trong quá trình phát triển mạng web thể giới www.

- Cách cài đặt Apache lên Windows:
    - Bước 1: **Download Apache** phiên bản 64 bit hoặc 32 bit.
    - Bước 2: Cài đặt Apache. Sau khi download thì tiến hành giải nén thư mục Apache24 vào ổ C.
    - Bước 3: Khởi động Apache: Vào thư mục **C:Apache24bin** và chạy file **httpd.exe**, khi có thông báo "**It works!**" hiện lên 
    hoặc nếu vào http://localhost kiểm tra thấy dòng "**It works!**" thì bạn đã cài đặt thành công.

##4. OpenServer
- OpenServer là phần mềm tạo webserver trên windows của Nga, và có rất nhiều tiện ích hay được tích hợp sẵn.
- OpenServer cung cấp cho người dùng rất nhiều nền tảng để kiếm tra sản phẩm của mình và chạy tốt trên tất cả những
môi trường.
- OpenServer có tích hợp sẵn các biến môi trường bên trong nó khi làm việc với Laravel.

- Download và cài đặt OpenServer
    - Bước 1: Truy cập "link" và chọn 1 file cài đặt và file cấu hình tương ứng để tải về và cài đặt.
    - Bước 2: Sau khi đã tải về ta sẽ có 1 file với tên Open_server_***.exe, bạn chạy file để bắt đầu cài đặt.
    - Bước 3: Cấu hình và sử dụng OpenServer.
    - Để dễ hình dung hơn về quá trình cài đặt, bạn vào [Link cài đặt](https://freetuts.net/cai-dat-openserver-va-tao-domain-ao-tren-localhost-281.html)
    
##5. PhpStorm


##6. Chrome dev tool

