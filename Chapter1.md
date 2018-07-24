#I. BLOCKCHAIN CƠ BẢN
##1. Định nghĩa, lịch sử của Blockchain
- Định nghĩa: 
	+ Theo góc nhìn kĩ thuật: 
		a. Blockchain là một quyển sổ cái đước chứa trong các node trong một mạng ngang hàng. Chỉ thêm mới dữ liệu. Rất khó để có thể chỉnh sửa. 
		b. Blockchain là một cấu trúc dữ liệu, nó chính là một linked list với hash pointer thay vì normal pointer
		c. Blockchain là một lớp trong hệ thống phân tán ngang hàng, Chạy trên TCP/IP. Tương tự đối với SMTP, HTTP, FTP...
	+ Theo góc nhìn từ doanh nghiệp: Blockchain là một nền tàng cho phép mọi người trao đổi nội dung thông qua các transaction mà không cần đặt niềm tin vào một đơn vị xác nhận trung gian
##2. Thành phần
#2.1. Address
Là đơn vị dùng để dịnh danh người gửi người nhận trong các transaction. Address thường là public key hoặc được tạo ra bằng public key
#2.2. Transaction
Là thành phần cơ bản của Blockchain. Chứa nội dung giao dịch giữa người nhận và người gửi
#2.3. Block
Block là thành phần bao gồm nhiều transaction, prev hash block, timestamp và gía trj nonc 
#2.4. Mạng ngang hàng
Là một kiểu mạng giúp các client trao đổi với nhau. Gửi và nhận thông tin
#2.5.Máy ảo
Là môi trường giả lập tách biệt trên các node. Nơi thực hiện các đoạn script trong một transaction. Nhiều hệ thống blockchain sử dụng VM như: EVM, CVM, NVM,...
#2.6. Nodes
Các node trong mạng blockchain thực hiện các chức năng nhất định, phụ thuộc vào chức vụ của chúng. Ví dụ: Xác nhận transaction, thực hiện mining thỏa mãn sự đồng thuận, bảo mật blockchain
#2.7. Smart contract
Là chương trình chạy trên nền tảng blockchain
##3. Đặc tính của blockchain
#3.1. Distributed consensus
- Thuật toán đồng thuận trên nền tảng phân tán tạo nên sức mạnh của blockchain. Tạo ra một nguồn thông tin chính xác duy nhất (single of truth) mà không cần một đợn vị xác thực trung tâm 
#3.2. Transaction verification
- Mọi transaction được gửi từ các node trong blockchain network đều được xác nhận dựa trên các điều kiện cho trước. Và chỉ được thêm vào blockchain khi thỏa mãn các yêu cầu đó
#3.3. Platforms for smart contract
- Là nền tảng cho phép lập trình viên phát triển ứng dụng smart contract trên nó. Tuy nhiên không phải tất cả blockchain đều hỗ trợ smart contract
#3.4. Transfering value between peers
- Blockchain hỗ trợ chuyển giá trị giữa các users thông qua token. Token là đơn vị đại diện cho giá trị trong nền tảng blockchain đó
#3.5. Generating cryptocurrency
- Blockchain có thể tạo ra tiền mã hóa nhằm mục đích khuyến khích các miner - những người đã bỏ tài nguyên ra để xác nhận giao dịch và củng cố tính bảo mật của blockchain
#3.6. Smart property
- Blockchain giúp tạo ra loại tài sản thông minh. Chỉ có chủ sở hữu nó mới có quyền sử dụng nó. Giải quyết vấn đề "doubled spent" và "double owned" của tài sản thông thường. Ví dụ như một file nhạc bản quyền có thể copy ra rất nhiều nơi
#3.7. Immutability
- Tính khó sửa đổi. Dữ liệu đã được thêm vào một blockchain rồi thì rất khó sửa đổi trừ phi sử dụng sức mạnh tính  toán không tưởng. Ví dụ trong bitcoin, phải sử dụng sức mạnh tính toán không lồ để tính toán lại proof of work của tất cả blocks trong blockchain, gần như là không tưởng
#3.8. Uniqueness
- Blockchain  đảm bảo rằng mọi transaction là duy nhất trong hệ thống. Và đảm bảo việc "double spending" không thể xảy ra
##4. Cách thức blockchain thêm mới block
1. Một node khởi tạo một transaction và sign với private key
2. Transaction được lan truyền tới các nodes thông qua gossip protocol. Các node này sẽ xác nhận transaction dựa trên các điều kiện cho trước (ví dụ như validate proof of work)
3. Khi transaction được xác nhận sẽ được vào một block và các block này sẽ được lan truyền trong mạng
##5. Các phiên bản blockchain
1. Blockchain 1.0 - Bitcoin và tiền mã hóa
2. Blockchain 2.0 - Ứng dụng trên hợp đồng thông minh (smart contract) cho ngành tài chính - tiền tệ
3. Blockchain 3.0 - Sự phát tán của blockchain 2.0 trong mọi lĩnh vưc trong xã hội: y tế, trường học,...
4. Blockchain X - Blockchain cho tất cả moi người. Sử dụng đơn giản như google search bây giờ
##6. Phân loại blockchain
##7. Điểm mạnh, điểm yếu về blockchain
##7. Nguyên lý CAP và Blockchain