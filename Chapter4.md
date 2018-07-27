#IV. Bitcoin

##1. Vòng đời của một transaction
- Người dùng gửi transaction thông qua các ứng dụng wallet
- Wallet sign transaction với private key của người dùng
- Signed transaction được lan truyền trong network với thuật toán flooding
- Các mining nodes thêm các transaction này vào 1 block mới để chuẩn bị cho việc mining
- Mining nodes thực hiện mining thoả mãn bài toán proof of work. Lan truyền block đã được mine ra network
- Các nodes khác trong mạng lưới thực hiện xác thực block và tiếp tục lan truyền. Số lượt xác nhận confirmation++
- Sau tối thiểu 6 lần confirmation, transaction được coi như đã được xác nhận. Số 6 có ý nghĩa trong việc chống lại double spending

##1. Cấu trúc của transaction
- MetaData: kích thước transaction, số lượng input, số lượng output, mã hash của transaction, version, lock_time - thời gian sớm nhất mà transaction được xác nhận
- Inputs: Mã hash của transaction trước đó, Txout-index, độ dài Txin-script, Txin-script
- Outputs: Quy định việc gửi bitcoin. Gồm 2 trường: trường số lượng bitcoin, trường locking script chứa điều kiện của transaction cần thiết của output transaction

##Cấu trúc của một block
- Block header
	- Version
	- Mã hash của block trước đó
	- Giá trị merkle root hash
	- Timestamp
	- Difficult target
	- Nonce
- Transaction count
- Transactions[]:


##2. Proof of work
- Bằng chứng cho việc bỏ ra nguồn tài nguyên tính toán để xây dựng một block mới. 
- Công thức tính PoW:
	`H (N || P_Hash || Tx || Tx ... || Tx) < Target`
	Trong đó:
	- N là số nonce
	- P_Hash là mã hash của block trước đó
	- Tx là mã hash của transation trong block đó
	- Target là độ khó cuả network
- Mục đính tìm ra số N thoả mãn nhỏ hơn độ khó Target. Tìm N bằng cách sử dụng brute-force
 
##3. Thuật toán mining
- Lấy mã hash của block trước đó
- Ghép các transaction chưa được verify vào chung 1 block
- Thực hiện băm block header mới (N = 0) tạo ra mã hash H
- Nếu mã hash H < độ khó H => Tiến hành lan truyền block mới => Kết thúc.
- Nếu mã hash H >= độ khó H => Tiến hành lặp lại với ++N

##Mining pools
- Lả tổ hợp các miners cùng thực hiện mining
- Miner A vẫn nhận được phần thưởng nếu chỉ có miner B mining đào thành công
- Phần thưởng được chia cho miners dựa trên lượng tài nguyên tính toán mà miner đó đã bỏ ra
- Một số mining pool lớn: AntPool, F2Pôl, BƯ.com

##Bitcoin network
###1. Các loại node
- Full node: wallet, miner, full blockchain storage, network routing
- Light node: wallet, network routing
 
###2. Cách hoạt động bitcoin network 
[View more](https://en.bitcoin.it/wiki/Bitcoin_Core_0.11_(ch_4):_P2P_Network)

##Wallet
- Ví wallet được sử dụng để lưu địa chỉ ví, public key hoặc private key. Có nhiệm vụ gửi, nhận bitcoin
- Các loại wallet: 
	- Ví không xác định: Loại ví này sẽ sinh các private key ngẫu nhiên
	- Vi xác định: Loại ví này sẽ sinh các private key dựa trên hàm băm giá trị seed. Seed là chuỗi các từ ngẫu nhiên từ chuẩn [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt). Ví dụ: MetaMask
	- Ví kế thừa xác định: Loại ví này lưu trữ các keys dưới dạng cây được sinh ra bởi private key
	- Ví con người: Loại ví này sinh private key bằng việc băm passphrase do người dùng nhập vào