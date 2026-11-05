# Bài Tập Thực Hành Session 17 - Lập Trình Web / Mạng Máy Tính

## 1. Phân tích hiện tượng Domino Effect từ việc tái sử dụng mật khẩu
- **Nguyên nhân cốt lõi:** Khi người dùng sử dụng chung một mật khẩu duy nhất (`123456`) cho nhiều dịch vụ khác nhau (diễn đàn nhỏ, Gmail, Facebook, GitHub), một dịch vụ nhỏ bất kỳ bị lộ cơ sở dữ liệu (Data Breach) sẽ vô tình mở toang cánh cửa cho hacker.
- **Cơ chế tấn công (Credential Stuffing):** Kẻ tấn công thu thập tập dữ liệu email và mật khẩu dạng plaintext hoặc mã hóa yếu từ diễn đàn bị hack. Ngay lập tức, chúng dùng các công cụ tự động (Bot) để thử cặp thông tin đăng nhập này hàng loạt lên các hệ thống lớn (Gmail, Facebook, GitHub). Do người dùng dùng chung một mật khẩu, hacker dễ dàng chiếm đoạt toàn bộ các tài khoản quan trọng khác mà không cần tốn công tấn công trực tiếp.

## 2. So sánh mật khẩu cảm tính và mật khẩu do máy tính sinh ra
- **Mật khẩu cảm tính (Human-generated):** Thường dựa trên ngày sinh, tên người thân, dãy số quen thuộc (`123456`, `Password@123`) hoặc từ có nghĩa. Không gian mẫu nhỏ, dễ bị các thuật toán dò vét cạn (Brute-force) hoặc tấn công từ điển (Dictionary Attack) đoán ra trong tích tắc.
- **Mật khẩu do máy tính sinh ra (Machine-generated):** Sử dụng tập ký tự ngẫu nhiên bao gồm chữ hoa, chữ thường, số và ký tự đặc biệt với độ dài lớn (từ 16-32 ký tự). Bất khả thi đối với các phương pháp vét cạn thông thường do tổ hợp khóa cực kỳ khổng lồ.

## 3. Tiêu chuẩn AES-256 và Quản lý mật khẩu (Password Manager)
- **Bản chất mã hóa AES-256:** Advanced Encryption Standard với khóa dài 256-bit là chuẩn mã hóa đối xứng cấp độ quân sự. Khối lượng tổ hợp khóa lớn đến mức toàn bộ siêu máy tính mạnh nhất hiện nay cũng không thể dò ra trong hàng tỷ năm.
- **Lý do Password Manager an toàn hơn ghi chép thủ công:**
  - *Ghi chép thủ công (sổ tay, file Word, ghi chú):* Dễ bị người khác đọc trộm, mất sổ, hoặc máy tính bị dính mã độc đánh cắp tệp văn bản.
  - *Password Manager (Két sắt số):* Mã hóa toàn bộ cơ sở dữ liệu bằng thuật toán AES-256 dựa trên một Master Passphrase duy nhất theo kiến trúc Zero-Knowledge. Máy chủ lưu trữ không bao giờ biết mật khẩu thật của người dùng, loại bỏ hoàn toàn rủi ro lộ lọt dữ liệu.
