```js
const { test, expect } = require('@playwright/test');

test.describe('Login_Form_UI_Test', () => {
  test('Kiểm tra giao diện form đăng nhập hiển thị đầy đủ các thành phần', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await expect(page).toHaveTitle(/Đăng nhập | Nexite Cloud/i);
    const emailLabel = page.locator('//label[contains(text(),"Email")]');
    await expect(emailLabel).toBeVisible();
    const usernameInput = page.locator('//input[@name="email"]');
    await expect(usernameInput).toBeVisible();
    const passwordLabel = page.locator('//label[contains(text(),"Mật khẩu")]');
    await expect(passwordLabel).toBeVisible();
    await expect(usernameInput).toBeEditable();
    const passwordInput = page.locator('//input[@name="password"]');
    await expect(passwordInput).toBeVisible();
    await expect(passwordInput).toBeEditable();
    const loginButton = page.locator(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    await expect(loginButton).toBeVisible();
    await expect(loginButton).toBeEnabled();
    const eyeButton = page.locator(`//button[@type='button' and @data-variant='subtle']`);
    await expect(eyeButton).toBeVisible();
    const registrationLink = page.locator(`//a[text()='Đăng ký']`);
    await expect(registrationLink).toBeVisible();
    const accountVerificationLink = page.locator(`//a[text()='Xác thực tài khoản']`);
    await expect(accountVerificationLink).toBeVisible();
    const forgotPasswordLink = page.locator(`//a[text()='Quên mật khẩu?']`);
    await expect(forgotPasswordLink).toBeVisible();
  });

});
test.describe('Login_Failure_Test', () => {
  test('Kiểm tra việc đăng nhập với thông tin sai để xác minh hiển thị thông báo lỗi', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydz@gmail.com');
    await page.fill('//input[@name="password"]', 'duydz123');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errorMessage = page.locator('//p[text()="Có lỗi xảy ra khi đăng nhập. Vui lòng thử lại sau."]');
    await expect(errorMessage).toBeVisible();
    await expect(errorMessage).toContainText(/Có lỗi xảy ra khi đăng nhập. Vui lòng thử lại sau./i);

  });

});
test.describe('Login_Field_Validation', () => {
  test('Để trống username, nhập password và nhấn đăng nhập', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', '');
    await page.fill('//input[@name="password"]', 'duydz123');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Vui lòng nhập tên đăng nhập"');
    await expect(errMsg).toBeVisible();
  });

  test('Nhập username, để trống password và nhấn đăng nhập', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydz@gmail.com');
    await page.fill('//input[@name="password"]', '');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Vui lòng nhập mật khẩu"');
    await expect(errMsg).toBeVisible();
  });

  test('Không nhập gì và nhấn nút đăng nhập', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', '');
    await page.fill('//input[@name="password"]', '');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Vui lòng nhập tên đăng nhập và mật khẩu"');
    await expect(errMsg).toBeVisible();
  });

  test('Nhập username sai định dạng và nhấn nút đăng nhập', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydzgmail.!');
    await page.fill('//input[@name="password"]', 'duydz123');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Tên đăng nhập không hợp lệ"');
    await expect(errMsg).toBeVisible();
  });

  test('Nhập mật khẩu ít hơn số ký tự tối thiểu', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydz@gmail.com');
    await page.fill('//input[@name="password"]', 'duyd');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Mật khẩu phải có ít nhất 6 ký tự"');
    await expect(errMsg).toBeVisible();
  });

  test('Nhập mật khẩu nhiều hơn số ký tự tối đa', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydz@gmail.com');
    await page.fill('//input[@name="password"]', 'duyd423542563637788262672457123141415255634626');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Mật khẩu phải có it hơn 34 ký tự"');
    await expect(errMsg).toBeVisible();
  });

  test('Nhập username nhiều hơn số ký tự tối đa', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydz13141452354562677872828qweqeqeqeqweqeqe@gmail.com');
    await page.fill('//input[@name="password"]', 'duydz12345');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Tên đăng nhập quá dài"');
    await expect(errMsg).toBeVisible();
  });

  test('Nhập username ít hơn số ký tự tối thiểu', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydz@gmail.com');
    await page.fill('//input[@name="password"]', 'duydz12345');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Tên đăng nhập quá ngắn"');
    await expect(errMsg).toBeVisible();
  });

  test('Nhập username, mật khẩu chứa ký tự đặc biệt và nhấn đăng nhập', async ({ page }) => {
    await page.goto('https://dash.nexite-cloud.com/signin?utm_source=home&utm_content=btn-header'); 
    await page.fill('//input[@name="email"]', 'duydz@gmail.com!@#$$%^&*()');
    await page.fill('//input[@name="password"]', '!@#$$%^&*()');
    await page.click(`//button[@type='submit' and .//span[text()='Đăng nhập']]`);
    const errMsg = page.locator('//p[text()="Không chứa kí tự đặc biệt"');
    await expect(errMsg).toBeVisible();
  });
});
```