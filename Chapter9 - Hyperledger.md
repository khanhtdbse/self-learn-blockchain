#IX. Hyperledger
##1. Giới thiệu 
- Là một dự án phát triển bởi The Linux Foundation. Nhằm mục đích xây dựng các bộ công cụ, framework open source trên nền tảng blockchain
- Gồm các dự án con
	- Hyperledger sawtooth: tập trung vào việc tách biệt sổ cái, thuật toán đồng thuận và các transaction. Bằng cách xây dựng transaction theo chuẩn transaction families, và có thể tuỳ chọn thuật toán đồng thuận cho các transaction này
	- Hyperledger fabric: nền tảng linh hoạt cho phép plug-and-play các thành phần của một hệ thống blockchain. Một số component: chaincode, blockchain, membership service, ..
	- Hyperledger indy: Cung cấp giải pháp định danh trên nền tảng blockchain
	- Hyperledger burrow: Tương tự với máy ảo của Ethereum (EVM). Tuy nhiên tích hợp thêm chức năng phân quyền

##2. Giới thiệu về hyperledger fabric
##2.1. Giới thiệu
- Mục đích:
	- Những người tham gia phải được định danh
	- Phân quyền tầng network
	- Hiệu năng, transaction/s cao
	- Xác nhận transaction với độ trễ thấp
	- Đảm bảo quyền riêng tư của transaction khi cần thiết
- Fabric có smart contract được viết bằng các khác ngôn ngữ khác nhau (Java, Go, NodeJS)

##2.2. Các service trong hyperledger fabric
####2.2.1 Membership service

- Chức năng:
	- Xác thực thông tin người dùng
	- Đăng ký người dùng
	- Gán quyền cho người dùng
- Gồm các component con:
	- Registration authority
	- Enrolment certificate authority
	- Transaction certificate authority
	- TLS certificate authority

####2.2.2. Blockchain service
- Gồm các component con
	- Consensus manager: Các consensus có sẵn: PBFT. SIEVE. NOOPS
	- Distributed ledger: Sổ cái được lưu dưới dạng key-value. Sử dụng RocksDB
	- Peer to peer protocol: Sử dụng gRPC

####.2.2.3. Chaincode service
- Gồm các component con
	- Secure container: Chaincode sẽ được thực thi trong container (thường sử dụng docker)
	- Secure registry: Chứa danh sách các chaincode
* Chaincode chính là smart contract. Gồm 4 function chính
	- Init(): Chạy khi chaincode được deploy
	- Invoke(func_name, func_params[]): Chạy khi call chaincode, có thể thực hiện hành động ghi dữ liệu vào sổ cái
	- Query(): Thực hiện để lấy dữ liệu từ sổ cái
	- Main(): Được chạy khi một peer deploy chaincode

##2.3. Hello world
- curl -­sSL https://goo.gl/byy2Qj | bash -­s 1.2
- cd first-network && ./byfn.sh -m generate
-  ./byfn.sh -m up
-  cd ../fabcar && npm i && npm i grpc
-  ./startFabric.sh
-  node enrollAdmin.js
-  node registerUser.js
-  node query.js
-  Edit call paramaters in invoke.js
-  node invoke.js
-  node query.js to view result

##2.4. Các mô hình

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/peers.diagram.1.png)
*Các peer gồm giữ các bản copy của sổ cái và sử dụng chung smart contract để tương tác với bản copy đó*

###2.4.1. Peer & application
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/peers.diagram.6.png)

*Ứng dụng A tương tác với Peer thông qua 2 loại*

*- Query transaction: A build transaction -> connect P1 -> invoke S1 -> response to -> A; Loại transaction này lấy được kết quả ngay lập tức*

*- Update transaction: A build transaction -> order in O1 -> collect transactions in block -> distribute to all peers -> all peers validated -> update event -> A; Loại transaction này không lấy được kết quả ngay lập tức do phải xác thực trên tất cả các peers*

###2.4.2. Peer & organization
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/peers.diagram.8.png)
*Các peers trong blockchain network có thể thuộc nhiều organization khác nhau. Blockchain network được tạo nên bởi các peers do các org đóng góp. Channel C kết nối các peers P1 P3 P5 P7 P8 với nhau. Network không tồn tại nếu không có các peers đóng góp*

###2.4.3. Peer & Identify
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/peers.diagram.9.png)

*Khi một peer kết nối tới channel C sử dụng digitial certificate. Channel C xác thực peer đó thông qua MSP để xác định nguồn tài nguyên mà peer đó có thể truy xuất. MSP là một component mapping giữa peer và org*

###2.4.4. Peer & Order
####Phase 1: Proposal
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/peers.diagram.10.png)

*Application A1 tạo transaction T1 -> gửi tới peer P1, P2 qua channel C -> P1, P2 lần lượt chạy smart contract S1, S2 ra response R1, R2 -> P1, P2 sign kết qủa R1, R2 bằng private key -> gửi tới A1 (do response có thể khác nhau giữa các peer, A1 có quyền loại bỏ các transaction không hợp lý)*

*Việc lựa chọn các peers phụ thuộc vào chính sách tán thành (endorsement policy) của smartcontract. EP định nghĩa danh sách các org cần thiết để xác nhận sự thay đổi của sổ cái trước khi chúng được xác nhận của network và được chấp nhận bởi các sổ cái khác*

####Phase 2: Packaging
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/peers.diagram.11.png)

*Order component gom các transaction từ các application khác nhau tạo thành một block (thứ tự transaction trong block có thể khác so với thời gian gom transaction đó, thứ tự này là bất biến). Khi block đạt đủ kích thước tối đa hoặc đạt đủ thời gian thì sẽ được phân bổ đến các peer thông qua channel C*

####Phase 3: Validation
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/peers.diagram.12.png)

*Order component phân bổ block B2 tới các peers thông qua channel C. Tại từng peer sẽ thực hiện xác thực từng transaction trong block thông qua việc xem xét các transaction được chấp nhận bởi các org trong chính sách tán thành (được lưu trong smartcontract). Transaction đã được xác thực sẽ được áp dụng vào sổ cái. Các peer sẽ phát ra các event tương ứng, các applications có thể subscribe các event này để xử lý*

*Lưu ý: Ở phase 3 này không chạy lại smartcontract. Việc chạy smartcontract chỉ chạy ở phase 1. Việc này đảm bảo tính mở rộng sau này: kết quả vẫn được đảm bảo bởi org trong chính sách tán thành mà không cần chạy smartcontract ở tất cả các peer*