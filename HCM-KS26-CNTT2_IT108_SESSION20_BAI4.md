

## 1. Bảng so sánh phương thức lưu trữ mật khẩu

| Tiêu chí | Lưu trực tiếp trên Google Chrome | Sử dụng Bitwarden (Dedicated Vault) |
| :--- | :--- | :--- |
| **Khả năng chống Infostealer** | **Kém.** Mã độc Infostealer dễ dàng giải mã và trích xuất tệp `Login Data` cục bộ của trình duyệt. | **Cao.** Dữ liệu két sắt được mã hóa AES-256 từ phía máy khách, chống lại việc đọc trộm dữ liệu thô. |
| **Kiến trúc Zero-Knowledge** | **Không.** Google có cơ chế kỹ thuật và có thể truy cập/quản lý dữ liệu đồng bộ tài khoản của người dùng. | **Có chuẩn mực.** Nhà cung cấp hoàn toàn không biết Master Passphrase hay dữ liệu giải mã của két sắt. |
| **Khả năng đồng bộ chéo nền tảng** | Bị giới hạn chủ yếu trong hệ sinh thái Google Chrome / Android. | Hỗ trợ đa nền tảng tuyệt đối (Windows, macOS, Linux, iOS, Android, Browser Extensions). |

## 2. Lập luận ưu thế bảo mật của Bitwarden
- Dù việc sử dụng Bitwarden đòi hỏi thêm một vài thao tác nhập Master Password hoặc mở khóa két sắt, nhưng mức độ bảo mật mang lại là vượt trội hoàn toàn. 
- Trình duyệt Chrome sinh ra để duyệt web, tệp chứa mật khẩu nằm ở dạng dễ bị khai thác bởi các dòng mã độc Infostealer hiện đại. Trong khi đó, Bitwarden cô lập hoàn toàn dữ liệu trong một két sắt mã hóa độc lập, chỉ giải mã trên RAM khi có khóa đúng của người dùng, bảo vệ doanh nghiệp trước các nguy cơ tấn công máy trạm.
