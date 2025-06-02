# Login Page

## Page Title
- **Login title:** `//h1[contains(text(),'Đăng nhập')]`

## Email Field
- **Label Email:** `//label[contains(text(),'Email')]`
- **Input Email:** `//input[@name='email']`

## Password Field
- **Label Password:** `//label[contains(text(),'Mật khẩu')]`
- **Input Password:** `//input[@name='password']`

## Nút và Liên kết
- **Login Button:** `//button[@type='submit' and .//span[text()='Đăng nhập']]`
- **Eye Button (show/hide password):** `//button[@type='button' and @data-variant='subtle']`
- **Registration Link:** `//a[text()='Đăng ký']`
- **Account Verification :** `//a[text()='Xác thực tài khoản']`
- **Link Forgot Password:** `//a[text()='Quên mật khẩu?']`
