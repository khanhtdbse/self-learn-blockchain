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
#6.1. Public blockchain
 - Là loại blockchain mở cho tất cả người dùng đều có thể tham gia với tư cách là một node và có quyền trong việc ra quyết định trong mạng lưới chung. Bản sao của sổ cái được lưu trữ, bảo trì tai tất cả các node
#6.2. Private blockchain
- Là loại blockchain chỉ cho một người hoặc nhóm người truy cập sổ cái
#6.3. Semi-private blockchain
- Là loại blockchain gồm 2 phần. Phần mở cho tất cả mọi người sử dụng và phần đóng chỉ cho một người hoặc một nhóm người sử dụng
#6.4. Sidechain
- Sidechain là một loại blockchain. Nó có thể nhận coin từ một blockchain khác (one way pegged sidechain) hoặc chuyển coin tới một blockchain khác (two ways sidechain)
- Thường áp dụng trong việc tạo ra các AltCoin (Alternative coin)
##7. Sự đồng thuận trong blockchain
#7.1. Khái niệm
- Sự động thuận là một nội dung trong hệ thống phân tán và hiện nay đã được áp dụng phổ biến trong blockchain nhằm mục đích tạo ra sự chính xác duy nhất (sing version of truth) được chấp nhận bởi tất cả các node trong network
- Phân loại
	+ Proof-based, leader-based: Leader node được bình chọn và đưa ra kết quả cuối cùng
	+ Byzantine fault tolerance-based: Dựa trên số lượng votes
#7.2. Một số thuật toán đồng thuận phổ biến
*a. Bằng chứng công việc (proof of work)*
- Dựa trên bằng chứng của việc sử dụng đủ nguồn tài nguyên tính toán trước khi đề xuất một giá trị nào đó để đạt được sự chấp nhật của network
- Hiện nay đã được áp trung bitcoin và một số tiền mã hóa khác
*b. Bằng chứng cổ phần (proof of stake)*
- Dựa trên lượng cổ phần của node đó trong network do đó lợi nhuận thu lại từ việc tấn công hệ thống trên PoS sẽ không bằng chi phí bỏ ra để mua lượng cổ phần lớn nhất
- Bắt đầu áp dụng từ Peercoin. Nay được áp dụng phổ biến trong Ethereum 
*c. Bằng chứng cổ phần ủy quyền (delegated proof of stake)*
- Các node có cổ phần trong network có quyền ủy quyền cho các nodes khác thực hiện xác nhận giao dịch bằng voting
*d. Bằng chứng thời gian hao tổn*
- Được giới thiệu bởi intel. Sử dụng Trusted Execution Environment (TEE) để chọn ra ngẫu nhiên an toàn một leader. Yêu cầu sử dụng Software Guard Extension
- Được áp dụng trong dự án Intel Sawtooth Lake blockchain
*e. Bằng chứng sự quan trọng*
- Bằng chứng sự quan trọng không những phụ thuộc vào cổ phần PoS mà còn phụ thuộc vào việc sử dụng tokens
- Áp dụng trong Nemcoin
*f. Thuận toán đồng thuận liên kết*
 - Các node trong mạng giữ một danh sách các nodes uy tín và chỉ lan truyền các transaction từ các nodes  uy tín đó
 *g. Thuận toán đồng thuận tín nhiệm*
 - 1 node được chọn để ra quyết định dựa trên sự tín nhiệm mà node đã tạo ra được trước đó
##8. Nguyên lý CAP và Blockchain
Blockchain đảm bảo được tính Availablity, Partition tolerance và Eventually Consistency
##9. Điểm mạnh, điểm yếu về blockchain
#9.1. ĐIểm mạnh
- Phân tán
- Đáng tin cậy nhờ nội dung trong suốt của các transaction
- Rất khó thể chỉnh sửa
- Uptime cao bởi rất nhiều nodes online
- Bảo mật cao nhờ thuật toán mã hóa tiên tiến
- Có ý nghĩa thống nhật cấu trúc CSDL cho các ngành khác nhau
- Tiết kiệm chi phí do không cần bên thứ 3 xác nhận
#9.2. Điểm yếu
- Khả năng mở rộng với dữ liệu lớn
- Khả năng áp dụng còn hạn chế
- Quyền riêng tư khi cần thiết
