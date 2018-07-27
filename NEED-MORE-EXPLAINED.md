#1. Gossip protocol
Gossip là một giao thức dùng để tìm ra vị trí và thông tin về trạng thái của các node khác đang tham gia vào cluster. Đây là một giao thức liên lạc dạng peer-to-peer trong đó mỗi node trao đổi định kỳ thông tin trạng thái của chúng với các node khác mà chúng có liên kết. Tiến trình gossip chạy mỗi giây. Các node thông đổi thông tin về chính chúng và cả thông tin với các node mà chúng đã trao đổi, bằng cách này toàn bộ những node có thể nhanh chóng hiểu được trạng thái của tất cả các node còn lại trong cluster. Một gói tin gossip bao gồm cả version đi kèm với nó, như thế trong mỗi lần trao đổi gossip, các thông tin cũ sẽ bị ghi đè bởi thông tin mới nhất ở một số node. Cách lan truyền của gossip protocol tương tự với việc lan truyền virus trong sinh học

#2. Sidechain
Sidechain hoạt động tương tự như một blockchain bình thường. Đều bắt đầu bằng một block khởi thuỷ (genesis block). Sidechain tự định nghĩa cấu trúc transaction, cho phép sử dụng smart contract hay không,.... Sidechain có thể private

Tuy nghiên sidechain phải đăng ký trên một mainchain theo cơ chế subscriber - observer. Sidechain lắng nghe sự kiện từ mainchain và thực hiện hành động nhất định

#3. Sybil attack
Trong mạng ngang hàng, người có chủ đích tấn công mạo nhận sẽ tạo một số lượng các nút ảo đủ lớn để tăng cường ảnh hưởng lên mạng. Mỗi một nút ảo mới sẽ đóng vai trò như là một phiếu bầu cho người tấn công.
![](https://i1.wp.com/sumup.news.cs.nyu.edu/index_files/vote2.jpg?zoom=2)

#4. Coin age in ethereum


- Practical byzantine fault tolerance
- Distributed hash tables (DHTs)
- Inter planetary file system (IPFS)
- Directed acyclic graph
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