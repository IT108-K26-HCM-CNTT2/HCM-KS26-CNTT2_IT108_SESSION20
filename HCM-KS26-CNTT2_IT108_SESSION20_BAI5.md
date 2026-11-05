# Bài Tập Thực Hành Session 17 - Lập Trình Web / Mạng Máy Tính

## 1. Thiết kế kiến trúc MFA & TOTP cho Crypto Wallet
- **Sơ đồ luồng dữ liệu bảo vệ 3 lớp:**
  ```text
  [ Người dùng giao dịch Crypto ]
         │
         ├── Lớp 1: Master Password / PIN (Thứ bạn biết)
         │      │
         │      ▼
         ├── Lớp 2: Thiết bị phần cứng / App TOTP - Google Authenticator (Thứ bạn có)
         │      │
         │      ▼
         └── Lớp 3: Sinh dữ liệu sinh trắc học / Xác thực giao dịch (Thứ là chính bạn)
  ```
- **Cơ chế phối hợp:** Khi hacker lấy được mật khẩu (Lớp 1), chúng vẫn hoàn toàn bất lực vì không sở hữu mã TOTP 6 chữ số thay đổi liên tục theo thời gian trên ứng dụng di động của người dùng (Lớp 2), kết hợp cùng xác thực sinh trắc học tại thiết bị cục bộ (Lớp 3).

## 2. Xử lý tình huống ngoại lệ (Edge Case): Đang ở trên máy bay không có Internet
- **Bản chất thuật toán TOTP (Time-based One-Time Password):** Không cần kết nối Internet hay sóng điện thoại để nhận mã.
- **Cách lấy mã OTP trên máy bay:** Ứng dụng Google Authenticator hoạt động hoàn toàn ngoại tuyến dựa trên đồng hồ thời gian thực (Timestamp) của điện thoại và khóa bí mật (Secret Key) đã được đồng bộ từ trước. Người dùng chỉ cần mở app lên là mã OTP vẫn sinh ra chính xác để thực hiện giao dịch bình thường mà không cần mạng.
