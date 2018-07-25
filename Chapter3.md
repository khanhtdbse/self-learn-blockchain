#III. Mã hoá và nền tảng công nghệ
##1. Symmetric cryptography
- Thuật toán mã hoá này dùng 1 key duy nhất để mã hoá và giải mã dữ liệu. Hay còn gọi là secret key cryptography
- Bao gồm 2 loại chính
	- Stream ciphers: RC4, A5
	- Block ciphers: Data Encryption Standard (DES), Advanced Encryptio Standard (AES)

###1.1. DES
![](https://www.tutorialspoint.com/cryptography/images/des_structure.jpg)
[View more](https://www.tutorialspoint.com/cryptography/data_encryption_standard.htm)

###1.2. AES
![](https://www.tutorialspoint.com/cryptography/images/aes_structure.jpg)
[View more](https://www.tutorialspoint.com/cryptography/advanced_encryption_standard.htm)
- Ví dụ
	- `openssl enc -aes-256-cfb -in msg.txt -out msg.bin`
	- `openssl enc -base64 -in msg.bin -out msg.b64`
	- `openssl enc -d -base64 -in msg.b64 -out msg.bin2`
	- `openssl enc -d -aes-256-cfb -in msg.bin2 -out msg.txt2`
##2. Asymmetric cryptography
- Thuật toán mã hoá này sử dụng 2 key riêng biệt. 1 key để mã hoá và 1 key để giải mã
- Các thuật toán phổ biến: RSA, ECC
![](https://i.stack.imgur.com/NEpCl.png)

###2.1. RSA
- Dựa trên vấn đề toán học: Nhân 2 số cực lớn rất dễ dàng nhưng rất khó để tìm ngược lại 2 số đó
- Ví dụ
	-  Tạo private key: `openssl genpkey -algorithm RSA -out privatekey.pem -pkeyopt rsa_keygen_bits:1024`
	-  Tạo public key từ private key: `openssl rsa -pubout -in privatekey.pem -out publickey.pem`
	- Mã hoá sử dụng public key: `openssl rsautl -encrypt -inkey publickey.pem -pubin -in msg.txt -out msg.rsa`
	- Giải mã sử dụng private key: `openssl rsautl -decrypt -inkey privatekey.pem -in msg.rsa -out msg.dec`

###2.2. ECC
- Dựa trên thuật toán đường cong elip
- Ví dụ: 
	-  Tạo private key: `openssl ecparam -name secp256k1 -genkey -noout -out ec-privatekey.pem`
	-  Tạo public key từ private key: `openssl ec -in ec-privatekey.pem -pubout -out ec-pubkey.pem`
	- Mã hoá sử dụng public key: `openssl rsautl -encrypt -inkey publickey.pem -pubin -in msg.txt -out msg.rsa`
	- Giải mã sử dụng private key: `openssl rsautl -decrypt -inkey privatekey.pem -in msg.rsa -out msg.dec`

##3. Hash function
###3.1. Khái niệm, tính chất
- Là hàm băm dữ liệu ra một đoạn mã băm có kích thước cố định. Được áp dụng để kiểm tra sự toàn vẹn của dữ liệu, lưu trữ mật khẩu, chia sẻ dữ liệu, virus finger print
- Một số hàm băm phổ biến: MD, SHA, RIPEMD
- Tính chất: 
	- Pre-image resistance: Tính không thể đảo ngược
	- Second pre-image resistance: Tính không thể tồn tại 2 input dữ liệu khác nhau tạo ra cùng 1 mã băm nếu chung 1 hàm băm
	- Collision resistance: Tính không thể tồn tại 2 mã băm với cùng dữ liệu đầu vào và hàm băm
- Ví dụ:
	- echo "text" | openssl dgst -sha256 // be183776c5b1e4359d0f5f6fca9d89170388874842034d8d5257627a723f2110	

###3.2. Phân loại hàm băm
- Message Digest (MD): hàm băm kém bảo mật. Thường được sử dụng để kiểm tra sự toàn vẹn của 1 file
- Secure Hash Algorithms (SHA)
	- SHA-0
	- SHA-1
	- SHA-2: SHA-224, SHA-256, SHA-512
	- SHA-3: SHA3-224, SHA3-256, SHA3-384
- RipeMD
- Whirlpool

##4. Chữ ký số (Digitial signature)
- Sử dụng với RSA:
	- Sign tài liệu: `openssl dgst -sha256 -sign privatekey.pem -out sign.bin msg.txt`
	- Verify tài liệu: `openssl dgst -sha256 -verify publickey.pem -signature sign.bin msg.txt` // Verified OK
- Sử dụng với ECC: Tương tự :)