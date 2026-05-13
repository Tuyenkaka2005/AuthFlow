<img width="210" alt="create-account" src="https://github.com/user-attachments/assets/8eec1f00-41f7-4db1-97a4-68ad6697c3c4" />
<img width="210" alt="reset-password" src="https://github.com/user-attachments/assets/a7d8fc9d-ba50-4404-b412-ef09657dd482" />
<img width="210" alt="interface-app" src="https://github.com/user-attachments/assets/97bb1677-34e0-4117-a4fb-bbee5b60e52c" />
<img width="210"  alt="dark-mode" src="https://github.com/user-attachments/assets/2708dd7d-fc5c-4ec9-9fe1-c988f175f890" />

# 🔐 AuthFlow — SwiftUI Authentication & Form Validation

**AuthFlow** là ứng dụng iOS mẫu triển khai luồng xác thực (Authentication Flow) hoàn chỉnh bằng **SwiftUI**, tuân thủ nghiêm ngặt các nguyên tắc **Clean Code** và tối ưu hóa Trải nghiệm Người dùng (**UX/UI**) trên nền tảng ứng dụng di động.

Dự án được xây dựng cho **LAB 4 — LOGIN & REGISTER FLOW**.

---

## 🚀 Tính năng nổi bật (Features)

### 1. Luồng chức năng chính (Core Flows)
* **Đăng nhập (Login Screen):** Giao diện trực quan, hỗ trợ quản lý bàn phím thông minh và tích hợp tính năng **Remember Me** (Bonus).
* **Đăng ký (Register Screen):** Nhập liệu thông tin cá nhân với cơ chế đối chiếu mật khẩu (Confirm Password) chuẩn xác.
* **Quên mật khẩu (Forgot Password Screen):** Luồng yêu cầu đặt lại mật khẩu với trạng thái phản hồi thành công thân thiện.
* **Màn hình chính (Home Screen):** Điều hướng bằng `.fullScreenCover` hiển thị thông tin lời chào cá nhân hóa sau khi đăng nhập thành công.

### 2. Trải nghiệm người dùng (UX) & Giao diện (UI)
* **Dynamic Validation:** Tách biệt hoàn toàn logic kiểm tra (Email Regex, độ dài Password) ra khỏi UI nhờ pattern `Validator`. Lỗi được hiển thị tức thì kèm animation mượt mà.
* **Smart Keyboard Management:** * Sử dụng `@FocusState` để tự động chuyển sang input tiếp theo khi nhấn Return/Next trên bàn phím.
  * Tự động ẩn bàn phím khi chạm vào vùng trống.
  * Đường viền (Border) và Icon của TextField tự động đổi màu highlight khi được focus.
* **Loading & Anti-Spam State:** Tích hợp `ProgressView` trực tiếp vào Component nút bấm, tự động vô hiệu hóa (`.disabled`) nút khi hệ thống đang xử lý để tránh spam API.
* **Dark Mode Support:** Giao diện tự động thích ứng hoàn hảo giữa chế độ Sáng và Tối nhờ tận dụng hệ thống màu bản địa của iOS (`.secondarySystemBackground`, `.secondary`, `.accentColor`).

---

## 📂 Cấu trúc dự án (Folder Structure)

Dự án áp dụng kiến trúc Module hóa UI, tách biệt rõ ràng giữa Dữ liệu (Models), Logic (Utilities), Thành phần tái sử dụng (Components) và Màn hình (Views).

```text
AuthFlow/
│
├── Models/
│   └── User.swift               # Mô hình dữ liệu người dùng
│
├── Utilities/
│   └── Validator.swift          # Logic kiểm tra tính hợp lệ của chuỗi (Email, Password)
│
├── Components/
│   ├── AuthTextField.swift      # Input nhập liệu chung (Hỗ trợ Icon, Focus state)
│   ├── PasswordField.swift      # Input mật khẩu (Hỗ trợ Show/Hide password)
│   ├── PrimaryButton.swift      # Nút bấm chính (Hỗ trợ Loading state, Animation)
│   └── ErrorText.swift          # Label hiển thị lỗi động
│
├── Views/
│   ├── LoginView.swift          # Màn hình đăng nhập
│   ├── RegisterView.swift       # Màn hình đăng ký tài khoản
│   ├── ForgotPasswordView.swift # Màn hình khôi phục mật khẩu
│   └── HomeView.swift           # Màn hình thành công (Sau khi xác thực)
│
└── AuthFlowApp.swift            # Root App Entry Point
