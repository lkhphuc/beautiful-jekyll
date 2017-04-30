---
layout: post
title: Tổng hợp cách tìm địa chỉ IP của Raspberry Pi
---

Nếu bạn mới bắt đầu làm quen và vọc vạch với chiếc Raspberry Pi, các bạn ắt hẳn đều sẽ đi tới bước yêu cầu có sử dụng địa chỉ IP của Raspberry Pi. Đối với nhiều bạn, hẳn sẽ vô cùng bối rối không biết địa chỉ IP là gì và làm sao để tìm và sử dụng nó. Trong bài này mình sẽ cùng các bạn tìm hiểu xem IP là gì, tại sao nhiều dịch vụ cần nó và các cách để tìm ra nó.

#Địa chỉ IP là gì?

Mỗi một thiết bị khi kết nối với một mạng nội bộ LAN (Local Area Network) đều sẽ được cấp một địa chỉ IP nội bộ (local IP address). Địa chỉ này có dạng X.X.X.X với X là 1 con số trong khoảng từ 0 tới 255 (8 bit), ví dụ: 192.168.0.255. Địa chỉ IP sẽ có nhiệm vụ phân biết giữa các thiết bị đang kết nối trong một network với nhau, nên trong cùng 1 network, 2 thiết bị sẽ không được cấp 2 địa chỉ IP giống nhau. Còn địa chỉ IP công cộng (public IP address) là địa chỉ IP của router nhà bạn trong network lớn nhất là Internet. Địa chỉ IP công cộng này sẽ được cấp bởi nhà cung cấp dịch vụ Internet (ISP- Internet Service Provider) của bạn như là Viettel, FPT,…
Như vậy, khi các bạn sử dụng các dịch vụ cần xác định đâu là Raspberry Pi của bạn trong 1 network, dịch vụ đó sẽ yêu cầu các bạn cung cấp địa chỉ IP của RPi. Các dịch vụ điển hình yêu cầu địa chỉ IP của Pi là SSH, FTP, VNC, Apache web server,…


#LÀM SAO ĐỂ TÌM ĐỊA CHỈ IP CỦA PI?

##Raspberry Pi có kết nối màn hình
Nếu bạn có thể nhìn thấy được màn hình của RPI thì các bạn chỉ cần bật Terminal lên và gõ lệnh:
			'$> ifconfig'
<hình>
Trong ví dụ trên 10.10.255.185 chính là địa chỉ IP của Pi.

##Raspberry Pi không có kết nối màn hình
Đôi khi bạn không có dư 1 chiếc màn hình để kết nối với Raspberry Pi nên bạn muốn sử dụng VNC để có thể hiện thị màn hình của Pi lên laptop, nhưng các dịch vụ như VNC yêu cầu IP address của RPi. Vậy bạn phải làm sao?

###Cách 1: tìm trực tiếp trên router
	Với cách này bạn có thể “mò” ra địa chỉ IP của Raspberry Pi trực tiếp từ trang web của Router nhà các bạn.
Yêu cầu: - 1 chiếc máy tính kết nối cùng network với RPi. -Quyền truy cập admin cục router nhà bạn.
Cách thực hiện chi tiết phương pháp này sẽ khác nhau tùy thuộc vào loại Router và số lượng thiết bị kết nối với router đó, tuy nhiên các bước thực hiện khá đơn giản và giống nhau.
####Bước 1: Từ 1  máy tính kết nối chung 1 network với Pi, bạn sẽ truy cập trang web điều khiển cục router bằng địa chỉ IP của cục router, thường sẽ được in lên trên cục router đó, vd: 192.168.0.1 . Sau đó các bạn đăng nhập vào sử dụng tài khoản admin. Hầu hết các router thông dụng có username và password mặc định là “admin”. 
####Bước 2: Từ đây các bạn di chuyển tới trang liệt kê toàn bộ các thiết bị đang được kết nối với nó. Trang này cụ thể nằm ở đâu thì phụ thuộc vào model của cục Router các bạn nhưng  thông thường sẽ được ghi là “Connected Devices” hay “DHCP clients”. Đặc điểm nhận dạng của trang này là sẽ có 1 loạt các địa chỉ IP của các thiết bị đã kết nối được liệt kê.

Ví dụ cục Tenda nhà mình nằm trong phần advance -> DHCP client. 
####Bước 3: Từ 1 danh sách các địa chỉ IP đã tìm được, bạn có thể nhận ra 1 vài thiết bị không phải là RPi và loại nó ra. Sau khi loại khỏi danh sách những địa chỉ chắc chắn không phải của Pi, bạn có thể thử lần lượt những địa chỉ còn lại, chắc chắn 1 trong số đó là của Pi nếu bạn đã cho Pi kết nối thành công với cục router. Nếu bạn kết nối với Pi bằng dây Ethernet, có thể bạn sẽ còn tìm ra IP dễ dàng hơn nữa. Trong trường hợp xấu nhất như trong hình trên là bạn không thể phân biệt được cái nào ra cái nào, bạn sẽ phải thử toàn bộ các IP trong đó. Ví dụ như trong hình trên, rất có khả năng RPi chính là thiết bị có hostname là JCH2BY………………
###Cách 2: Tìm trên máy tính Linux.
Cách này chúng ta sẽ sử dung Nmap (Network Mapping) Tool. Để sử dụng tool này các bạn nên kết nối máy tình linux của mình với chung network đã được kết nối với Pi.
####Bước 1: Các bạn sẽ tải phần mềm này về máy tính linux qua câu lệnh trên máy tính Linux: 
$> sudo apt-get install nmap
####Bước 2: Tìm địa chỉ IP của máy linux (tương tự cách tìm IP của Raspberry Pi có kết nối màn hình)
$> ifconfig

Như trên hình thì bạn có thể thấy địa chỉ IP máy mình là 10.10.255.185.
####Bước 3: Tìm địa chỉ IP Pi.
Vì Pi được kết nối chung 1 network với máy tính linux ở trên nên ta biết chắc chắn là địa chỉ IP của Pi sẽ giống với địa chỉ máy Linux 3 số đầu tiên. Ví dụ ở trên mình tìm được IP của máy tính linux là 10.10.255.185 thì địa chỉ Ip của Pi sẽ là: 10.10.255.x. Để tìm X, chúng ta sẽ sử dụng công cụ nmap theo câu lệnh:
$> nmap 10.10.255.1/24
Các bạn lưu ý thay 10.10.255 trong câu lệnh trên bằng 3 số đầu tiên trong địa chỉ IP mà bạn đã tìm được ở bước 2.

Kết quả của nmap, như trong ví dụ ta thấy có 4 địa chỉ IP, 1 trong số đó chính là IP của máy tính linux. Có 1 địa chỉ trong hình có service iphone-sync nên bạn biết chắc đó không phải địa chỉ của Pi. Nếu bạn để tên hostname mặc định là raspberrypi thì bạn có thể nhìn ra ngay địa chỉ Ip của Pi mà không cần phải đoán thêm.
###Cách 3: Tìm trên máy tính Windows.
Để tìm địa chỉ IP trên máy tính Windows, Raspberry Pi Việt Nam đã có 1 bài viết hướng dẫn ở đây, các bạn có thể xem qua.

------------------
Qua bài viết này mình hi vọng các bạn đã học thêm được nhiều điều về kiến thức mạng máy tính và biết thêm được nhiều cách tìm địa chỉ IP của Pi để tùy từng trường hợp mà sử dụng. Nếu có thắc mắc gì các bạn cứ comment xuống đây mình sẽ cố gắng hỗ trợ. Chúc các bạn vọc vạch vui vẻ.
