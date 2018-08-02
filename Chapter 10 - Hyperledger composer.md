#Hyperledger composer
#1. Giới thiệu

- Hyperledger composer là bộ công cụ giúp việc phát triển ứng dụng trên nền tảng blockchain trở nên dễ dàng hơn. Composer giúp định nghĩa business network model và giúp dễ dàng tích hợp với hệ thống có sẵn bên ngoài
![](https://hyperledger.github.io/composer/latest/assets/img/Composer-Diagram.svg) 

#2. Cấu trúc
- Blockchain State Storage: Tất cả các transaction được submit qua business network được lưu trữ tại sổ cái và state của assets, participants được lưu tại state database. Sổ cái và state database có tinh nhất quán giữa các peer nhờ thuật toán đồng thuận

- Connection Profiles: Là một file JSON dùng để kết nối tới hệ thống, do hệ thống sinh ra

- Assets: Là tài sản vô hình hoặc hữu hình được thể hiện trong business network. Tài sản phải phải có định danh ID riêng biệt, tài sản này có thể liên quan tới tài sản khác hoặc thực thể tham gia 

- Participants: Thực thể tham gia là một trong những thành phần của business network. Chúng có thể có tài sản và submit transaction. Tương tự như tài sản, chúng phải có định danh riêng biệt

- Identities: Là các chứng chỉ số cần thiết để các thực thể tham gia trong business network thực hiện giao dịch. Chứng chỉ số được map với thực thể tham gia

- Business Network cards: Gồm các thành phần: định danh, connection profile, metadata (chứa tên của businesss network cần kết nối,..). BNC nhằm đơn giản hóa việc kết nối tới business network, quản lý định danh

- Transactions: Là cơ chế thực thể tham gia tương tác với tài sản

- Queries: Dùng để lấy dữ liệu từ world state, có thể gồm nhiều tham số. Queries được gửi thông qua hyperledger composer API

- Events: Là các event được định nghĩa trong business network. Event sẽ được bắn ra với từng sự kiện cụ thể. Các application có thể subscribe các event này để xử lý.

- Access Control: Business network chứa các rules kiểm soát truy cập. Giới hạn tương tác giữa thực thể tham gia với tưng tài sản nhất định.

- Historian registry: Lưu trữ các transactions thành loại tài sản HistorianRecord
