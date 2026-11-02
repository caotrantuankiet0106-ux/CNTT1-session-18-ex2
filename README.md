# BÁO CÁO: SỰ CỐ PHIÊN LÀM VIỆC HỆ THỐNG VẬN TẢI GREENLOGISTICS

---

## Phần 1. Phân tích: Cache vs. Cookies

| Tiêu chí | Cache | Cookies |
| :--- | :--- | :--- |
| **Dung lượng** | Lớn (vài MB đến vài GB). | Rất nhỏ (tối đa ~4KB mỗi mẩu tin). |
| **Mục đích** | Lưu trữ tạm thời tài nguyên tĩnh (ảnh, CSS, JS) để tăng tốc độ tải trang. | Lưu trữ thông tin định danh và token phiên làm việc để duy trì trạng thái đăng nhập. |

---

## Phần 2. Triển khai: Cấu trúc mẩu tin Cookie
* **Token định danh:** `session_token=xyz789_secure_auth`
* **Thời gian sống:** `Max-Age=604800` (Lưu kéo dài 7 ngày, giúp shipper không bị mất phiên khi đóng trình duyệt).
* **Cờ bảo mật:**
  * `HttpOnly`: Ngăn chặn JavaScript (XSS) truy cập cookie.
  * `Secure`: Chỉ truyền qua kết nối HTTPS mã hóa.

---

## Phần 3. Kiểm thử: Xử lý sự cố Cache đệm
* **Thao tác Hard Reload:** Nhấn tổ hợp phím **`Ctrl + Shift + R`** (trên Windows) hoặc **`Cmd + Shift + R`** (trên macOS) để buộc trình duyệt bỏ qua cache cũ và tải lại toàn bộ tài nguyên mới nhất từ server.