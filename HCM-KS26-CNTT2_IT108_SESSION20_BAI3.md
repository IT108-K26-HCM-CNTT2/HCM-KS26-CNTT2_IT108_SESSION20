# Bài Tập Thực Hành Session 17 - Lập Trình Web / Mạng Máy Tính

## 1. Báo cáo phân tích (IPO) khôi phục tài khoản bằng Backup Codes
- **Input:** 
  - Chuỗi Mã dự phòng (Backup Codes / Recovery Codes) đã được hệ thống cấp sẵn và lưu trữ ngoại tuyến từ trước khi mất điện thoại.
  - Tài khoản đăng nhập AWS có yêu cầu xác thực MFA.
- **Process (Quy trình xử lý):**
  1. *Xác thực mã dự phòng:* Người dùng nhập một mã dự phòng độc nhất (mỗi mã chỉ dùng được 1 lần duy nhất) vào giao diện đăng nhập MFA.
  2. *Hủy mã cũ:* Hệ thống AWS ngay lập tức vô hiệu hóa mã vừa sử dụng để kẻ gian không thể dùng lại lần thứ hai.
  3. *Cấp quyền & Cấp mã mới:* Hệ thống cấp quyền truy cập vào bảng điều khiển (Console) để quản trị viên cấu hình lại thiết bị Authenticator mới, đồng thời cung cấp bộ mã dự phòng mới.
- **Output:** Khôi phục thành công quyền kiểm soát tài khoản AWS, vô hiệu hóa thiết bị cũ bị mất, hệ thống đảm bảo an toàn tuyệt đối.

## 2. Tại sao tuyệt đối không lưu Backup Codes dưới dạng ảnh trong thư viện điện thoại?
- **Nguy cơ từ ứng dụng bên thứ ba:** Khi lưu ảnh chụp màn hình chứa Backup Codes vào thư viện ảnh, các ứng dụng mạng xã hội, chỉnh sửa ảnh hoặc app độc hại được cấp quyền đọc thư viện (Storage Permission) có thể âm thầm quét và tải bức ảnh đó lên máy chủ của kẻ tấn công.
- **Rủi ro khi mất máy:** Nếu kẻ gian nhặt được điện thoại và mở được khóa màn hình (hoặc thiết bị không đặt mật khẩu khóa), chúng sẽ dễ dàng tìm thấy album ảnh chứa toàn bộ mã dự phòng, từ đó vượt qua lớp bảo vệ MFA của tất cả tài khoản quan trọng.
