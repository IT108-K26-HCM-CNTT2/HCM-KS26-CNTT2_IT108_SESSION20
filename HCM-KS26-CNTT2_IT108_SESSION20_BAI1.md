# Báo cáo Phân tích Chuỗi URL Giả mạo và Quy trình Kiểm tra An toàn

## 1. Phân tích Ký tự lạ trong URL và Cơ chế Lừa đảo (Homograph Attack)

### Ký tự lạ được phát hiện
* Trong chuỗi URL `https://githúb.com/login`, ký tự lạ nằm ở chữ **`ú`** (`U+00FA` - Latin Small Letter U with Acute) thay thế cho chữ **`u`** chuẩn (`U+0075` - Latin Small Letter U).

### Lý do kỹ thuật khiến người dùng dễ bị đánh lừa
1. **Sự tương đồng về thị giác (Visual Similarity):**
   * Trên các màn hình hiển thị tiêu chuẩn hoặc font chữ của trình duyệt web, dấu sắc trên chữ `ú` rất nhỏ và khó phát hiện nếu chỉ lướt qua nhanh.
   * Mắt người có xu hướng đọc cả từ theo thói quen nhận diện hình ảnh thay vì soi từng ký tự lẻ, nên dễ tự động "bỏ qua" dấu sắc và đọc thành `github.com`.

2. **Cơ chế hiển thị mã hóa Punycode của trình duyệt:**
   * Hệ thống tên miền quốc tế (IDN) cho phép dùng ký tự có dấu trong domain. 
   * Trên hệ thống DNS, tên miền này thực tế được chuyển thành dạng Punycode: `xn--githb-7ua.com`.
   * Tuy nhiên, các trình duyệt hiện đại lại mặc định hiển thị dạng Unicode (`githúb.com`) trên thanh địa chỉ để thân thiện với người dùng. Chính tính năng này đã vô tình tạo điều kiện cho hình thức tấn công giả mạo giao diện (Homograph attack) trông cực kỳ giống thật.

---

## 2. Quy trình Kiểm tra URL Nhanh Trước khi Nhập Mật khẩu / Master Password

Để tránh bị mất tài khoản khi gặp các thông báo cảnh báo giả mạo, quy trình kiểm tra được chia làm 2 bước chính:

### Bước 1: Kiểm tra nhanh bằng mắt thường (Manual Check)
1. **Soi kỹ tên miền chính (Domain Name):**
   * Nhấp chuột vào thanh địa chỉ để xem đầy đủ chuỗi URL.
   * Kiểm tra kỹ phần tên miền nằm ngay trước đuôi `.com`, `.net`, `.org`... Chú ý các cặp ký tự hay bị thay thế để lừa mắt như: `u` / `ú`, `a` / `α`, `o` / `0`, `l` / `1` / `I`.
2. **Kiểm tra ngữ cảnh và nguồn đường link:**
   * Không bao giờ bấm trực tiếp vào link đăng nhập gửi kèm từ Email cảnh báo hoặc tin nhắn bất ngờ.
   * Tất cả thông báo "Security Alert" nên được kiểm tra bằng cách tự gõ địa chỉ trang web gốc (`github.com`) vào tab mới hoặc dùng Bookmark đã lưu từ trước.

### Bước 2: Sử dụng công cụ hỗ trợ tự động (Automated Verification)
1. **Sử dụng Trình quản lý mật khẩu (Password Manager):**
   * Trình quản lý mật khẩu (như Bitwarden, 1Password, hoặc tính năng lưu mật khẩu của trình duyệt) nhận diện website dựa trên domain gốc chuẩn xác.
   * Nếu trang web là `githúb.com` (`xn--githb-7ua.com`), công cụ sẽ **không tự động điền (Auto-fill)** tài khoản/mật khẩu. Nếu thấy công cụ không tự điền như mọi khi, đây là dấu hiệu 100% trang web bị giả mạo.
2. **Kiểm tra Chứng chỉ số SSL/TLS (Digital Certificate):**
   * Bấm vào biểu tượng ổ khóa cạnh thanh địa chỉ.
   * Xem thông tin người sở hữu chứng chỉ (Subject/Issuer). Với các trang lớn như GitHub, chứng chỉ thường được cấp rõ ràng cho tổ chức sở hữu, còn trang giả mạo thường chỉ dùng chứng chỉ miễn phí ngắn hạn và tên tổ chức không khớp.
3. **Cài đặt tiện ích mở rộng an ninh mạng (Security Extensions):**
   * Sử dụng các extension cảnh báo lừa đảo như Netcraft Extension, uBlock Origin hoặc bật tính năng Safe Browsing nâng cao trên trình duyệt để tự động chặn các tên miền Punycode nghi vấn.