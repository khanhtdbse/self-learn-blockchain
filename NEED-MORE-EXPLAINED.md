#1. Gossip protocol
Gossip là một giao thức dùng để tìm ra vị trí và thông tin về trạng thái của các node khác đang tham gia vào cluster. Đây là một giao thức liên lạc dạng peer-to-peer trong đó mỗi node trao đổi định kỳ thông tin trạng thái của chúng với các node khác mà chúng có liên kết. Tiến trình gossip chạy mỗi giây. Các node thông đổi thông tin về chính chúng và cả thông tin với các node mà chúng đã trao đổi, bằng cách này toàn bộ những node có thể nhanh chóng hiểu được trạng thái của tất cả các node còn lại trong cluster. Một gói tin gossip bao gồm cả version đi kèm với nó, như thế trong mỗi lần trao đổi gossip, các thông tin cũ sẽ bị ghi đè bởi thông tin mới nhất ở một số node. Cách lan truyền của gossip protocol tương tự với việc lan truyền virus trong sinh học

#2. Sidechain
Sidechain hoạt động tương tự như một blockchain bình thường. Đều bắt đầu bằng một block khởi thuỷ (genesis block). Sidechain tự định nghĩa cấu trúc transaction, cho phép sử dụng smart contract hay không,.... Sidechain có thể private

Tuy nghiên sidechain phải đăng ký trên một mainchain theo cơ chế subscriber - observer. Sidechain lắng nghe sự kiện từ mainchain và thực hiện hành động nhất định

#3. Sybil attack
Trong mạng ngang hàng, người có chủ đích tấn công mạo nhận sẽ tạo một số lượng các nút ảo đủ lớn để tăng cường ảnh hưởng lên mạng. Mỗi một nút ảo mới sẽ đóng vai trò như là một phiếu bầu cho người tấn công.
![](https://i1.wp.com/sumup.news.cs.nyu.edu/index_files/vote2.jpg?zoom=2)

#4. Coin age in ethereum

#5.	Inter planetary file system (IPFS)
- Là một file system phân tán. Lưu file thành các mảnh nhỏ liên kết với nhau bằng mã hash của các mảnh đó.
- Kết hợp với blockchain để lưu file bảo mật. Lưu mã hash của file vào trong transaction của blockchain:
![](https://cdn-images-1.medium.com/max/1600/1*yzYjtRViCDeWyhGnVzsUYw.png)
	- John wants to upload a PDF file to IPFS but only give Mary access
	- He puts his PDF file in his working directory and encrypts it with Mary’s public key
	- He tells IPFS he wants to add this encrypted file, which generates a hash of the encrypted file
	- His encrypted file is available on the IPFS network
	- Mary can retrieve it and decrypt the file since she owns the associated private key of the public key that was used to encrypt the file. A malicious party cannot decrypt the file because they lack Mary’s private key


- Practical byzantine fault tolerance
- Distributed hash tables (DHTs)
- - Directed acyclic graph
- Filecon
- Bitswap
- BigchainDB
- Maidsafe
- Lisk
- Diffie - Hellman
- Elliptic curve cryptography
- Double spending
- Codius.org
- PBFT protocol
- SIEVE algorithm
- NOOPS
- Sawtooth lake intel
- Web3.js
- Truffle