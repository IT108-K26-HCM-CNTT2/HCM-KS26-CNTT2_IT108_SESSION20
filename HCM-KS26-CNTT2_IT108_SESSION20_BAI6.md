# Bài Tập Thực Hành Session 17 - Lập Trình Web / Mạng Máy Tính

## 1. Pre-push Checklist rà soát API Keys
- [ ] Kiểm tra toàn bộ mã nguồn trước khi push bằng công cụ quét tự động (`git-secrets` hoặc `trufflehog`).
- [ ] Đảm bảo không có chuỗi khóa bí mật nào bắt đầu bằng `sk-`, `key-`, `token-`, hoặc các chuỗi chuỗi kết nối Database chứa password dạng plaintext trong code.
- [ ] Xác nhận tệp `.env` đã được khai báo nằm hoàn toàn trong `.gitignore`.

## 2. Cấu trúc tệp `.env.example` chuẩn chuyên nghiệp
```env
# ==========================================
# MÔ HƯỚNG DẪN CẤU HÌNH MÔI TRƯỜNG (.env.example)
# ==========================================
PORT=3000
NODE_ENV=development

# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_USER=root
DB_PASSWORD=your_database_password_here
DB_NAME=ecommerce_db

# External API Keys & Services
STRIPE_API_KEY=sk_test_your_stripe_key_here
AWS_ACCESS_KEY_ID=your_aws_access_key_here
AWS_SECRET_ACCESS_KEY=your_aws_secret_key_here
JWT_SECRET=your_jwt_secret_signature_here
```

## 3. Hướng dẫn team kích hoạt bắt buộc 2FA trên GitHub
1. Truy cập vào **GitHub Organization** của dự án ➔ Chọn mục **Settings**.
2. Tìm đến phần **Security** ➔ Chọn **Member privileges**.
3. Tích chọn ô **Require two-factor authentication for all members of this organization**.
4. Lưu thay đổi. Hệ thống sẽ tự động gửi thông báo yêu cầu tất cả thành viên trong nhóm phải bật 2FA mới được phép tiếp tục commit/push mã nguồn vào repository của dự án.
