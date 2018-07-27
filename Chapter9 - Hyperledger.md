#IX. Hyperledger
##1. Giới thiệu 
- Là một dự án phát triển bởi The Linux Foundation. Nhằm mục đích xây dựng các bộ công cụ, framework open source trên nền tảng blockchain
- Dự án 6 dự án con
	- Hyperledger sawtooth: tập trung vào việc tách biệt sổ cái, thuật toán đồng thuận và các transaction. Bằng cách xây dựng transaction theo chuẩn transaction families, và có thể tuỳ chọn thuật toán đồng thuận cho các transaction này
	- Hyperledger fabric: nền tảng linh hoạt cho phép plug-and-play các thành phần của một hệ thống blockchain. Một số component: chaincode, blockchain, membership service, ..
	- Hyperledger indy: Cung cấp giải pháp định danh trên nền tảng blockchain
	- Hyperledger burrow: Tương tự với máy ảo của Ethereum (EVM). Tuy nhiên tích hợp thêm chức năng phân quyền

##2. Giới thiệu về hyperledger fabric
###2.1. Membership service
- Chức năng:
	- Xác thực thông tin người dùng
	- Đăng ký người dùng
	- Gán quyền cho người dùng
- Gồm các component con:
	- Registration authority
	- Enrolment certificate authority
	- Transaction certificate authority
	- TLS certificate authority

###2.2. Blockchain service
- Gồm các component con
	- Consensus manager: Các consensus có sẵn: PBFT. SIEVE. NOOPS
	- Distributed ledger: Sổ cái được lưu dưới dạng key-value. Sử dụng RocksDB
	- Peer to peer protocol: Sử dụng gRPC

###2.3. Chaincode service
- Gồm các component con
	- Secure container: Chaincode sẽ được thực thi trong container (thường sử dụng docker)
	- Secure registry: Chứa danh sách các chaincode
* Chaincode chính là smart contract. Gồm 4 function chính
	- Init(): Chạy khi chaincode được deploy
	- Invoke(func_name, func_params[]): Chạy khi call chaincode, có thể thực hiện hành động ghi dữ liệu vào sổ cái
	- Query(): Thực hiện để lấy dữ liệu từ sổ cái
	- Main(): Được chạy khi một peer deploy chaincode
