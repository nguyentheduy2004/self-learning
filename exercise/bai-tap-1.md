# Trang Đăng Nhập

## Tiêu đề trang
- **Đăng nhập:** `//h1[contains(text(),'Đăng nhập')]`

## Trường Email
- **Nhãn Email:** `//label[contains(text(),'Email')]`
- **Ô nhập Email:** `//input[@name='email']`

## Trường Mật khẩu
- **Nhãn Mật khẩu:** `//label[contains(text(),'Mật khẩu')]`
- **Ô nhập Mật khẩu:** `//input[@name='password']`

## Nút và Liên kết
- **Nút Đăng nhập:** `//button[@type='submit' and .//span[text()='Đăng nhập']]`
- **Nút Mắt (hiện/ẩn mật khẩu):** `//button[@type='button' and @aria-hidden='true']`
- **Liên kết Đăng ký:** `//a[text()='Đăng ký']`
- **Liên kết Xác thực tài khoản:** `//a[text()='Xác thực tài khoản']`
- **Liên kết Quên mật khẩu:** `//a[text()='Quên mật khẩu?']`
