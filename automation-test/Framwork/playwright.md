
# Tìm hiểu về Playwright
Playwright là một framework kiểm thử tự động do Microsoft phát triển, dùng để tự động hóa các trình duyệt web như Chromium (Chrome, Edge), Firefox và WebKit (Safari).
## Đặc điểm nổi bật
| Đặc điểm                          | Mô tả                                                                 |
|----------------------------------|----------------------------------------------------------------------|
| **Đa trình duyệt**             | Hỗ trợ Chromium, Firefox, WebKit (Safari). Chạy được trên nhiều hệ điều hành. |
| **Hỗ trợ đa tab / đa page**    | Có thể mở và điều khiển nhiều tab hoặc trang cùng lúc.               |
| **Tích hợp sẵn headless mode** | Chạy không giao diện (headless) để tăng tốc độ kiểm thử.             |
| **Tốc độ cao, ổn định**        | Rất nhanh và ít flakey (không ổn định) hơn so với Selenium.          |
| **Hỗ trợ nhiều ngôn ngữ**      | Viết test bằng JavaScript, TypeScript, Python, C#, Java.             |
| **Tích hợp record & codegen**  | Ghi lại thao tác người dùng và tạo sẵn mã test (`codegen`).          |
| **Tự động chờ (auto-wait)**    | Tự động đợi phần tử sẵn sàng (hiển thị, click được...) trước khi thao tác. |
| **Hỗ trợ test API**            | Cho phép gửi và kiểm tra request/response như Postman.               |
| **Snapshot, Video, Screenshot**| Tích hợp ghi lại video, chụp ảnh để debug khi test fail.             |
| **Tích hợp CI/CD dễ dàng**     | Dùng tốt với GitHub Actions, GitLab CI, Jenkins,...                  |
| **Hỗ trợ testing trên mobile** | Có thể giả lập thiết bị di động như iPhone, Pixel,...                |
| **Báo cáo kết quả trực quan**  | Giao diện hiển thị report rất dễ đọc và phân tích lỗi.               |
## 1. Các cài đặt, khởi tạo, chạy và xem report của playwrightplaywright
**cài đặt Playwright**:
```bash
npm install -D @playwright/test
npx playwright install
```
**Khởi tạo project**:
```bash
npm init playwright@latest
```
### Chạy toàn bộ test
  ```bash
  npx playwright test
  ```

### Chạy 1 file cụ thể
  ```bash
  npx playwright test tests/example.spec.js
  ```
### xem report
```bash
npx playwright show-report
```

---
## 2. So sánh Playwright và Selenium

Dưới đây là **so sánh chi tiết giữa Playwright và Selenium** — hai framework test tự động phổ biến nhất hiện nay:

| Tiêu chí                 | Playwright                                  | Selenium                                   |
|--------------------------|---------------------------------------------|--------------------------------------------|
| **Ngôn ngữ hỗ trợ**       | JavaScript/TypeScript, Python, C#, Java     | Hỗ trợ rất nhiều: Java, C#, Python, Ruby, JS, PHP... |
| **Trình duyệt hỗ trợ**    | Chromium, Firefox, WebKit (Safari)           | Hầu hết trình duyệt phổ biến (Chrome, Firefox, Edge, Safari, IE...) |
| **Cơ chế điều khiển trình duyệt** | Giao tiếp trực tiếp với trình duyệt qua DevTools protocol, hỗ trợ tự động chờ (auto-wait), điều khiển đa trình duyệt tốt | Sử dụng WebDriver giao tiếp qua trình duyệt, có thể chậm và phức tạp hơn |
| **Tính năng tự động chờ (waiting)** | Tự động chờ các sự kiện DOM, AJAX, animation giúp giảm flaky test | Cần phải code thủ công hoặc dùng thư viện bên ngoài để handle chờ đợi |
| **Tốc độ thực thi**       | Nhanh hơn do giao tiếp trực tiếp và hỗ trợ chạy song song | Thường chậm hơn, giao tiếp qua WebDriver tốn thời gian hơn |
| **Setup & cấu hình**     | Dễ dàng, có CLI hỗ trợ, tích hợp tốt với nhiều ngôn ngữ | Phức tạp hơn, nhiều bước cấu hình, driver cần tải riêng (chromedriver, geckodriver...) |
| **Hỗ trợ test đa trình duyệt** | Hỗ trợ cả Chromium, Firefox, WebKit (Safari) với API đồng nhất | Hỗ trợ nhiều trình duyệt, nhưng cần driver riêng cho từng trình duyệt |
| **Hỗ trợ test mobile**   | Hỗ trợ giả lập WebKit cho iOS, có thể tích hợp test web mobile | Selenium có Appium để test mobile nhưng là tool riêng biệt |
| **Quay video & chụp ảnh màn hình** | Hỗ trợ ghi video test và screenshot tích hợp sẵn | Cần setup thủ công hoặc dùng tool bên ngoài |
| **Cộng đồng & độ phổ biến** | Mới hơn, cộng đồng đang phát triển nhanh | Rất lớn, lâu đời, nhiều tài liệu và plugin hỗ trợ |
| **Khả năng mở rộng**     | Hỗ trợ tốt với các CI/CD pipelines hiện đại, dễ tích hợp | Rất tốt, được dùng rộng rãi trong doanh nghiệp lớn |
| **Độ ổn định test (Flaky test)** | Ít flaky hơn nhờ tự động chờ và API hiện đại | Dễ bị flaky test nếu không xử lý chờ đợi tốt |

---
## 3.So sánh Framework vs Tool

| Tiêu chí              | Framework                                                  | Tool                                                        |
|-----------------------|------------------------------------------------------------|-------------------------------------------------------------|
| **Khái niệm**         | Là một **bộ khung** gồm nhiều thư viện, cấu trúc sẵn để phát triển hoặc kiểm thử | Là **công cụ đơn lẻ** hỗ trợ thực hiện một tác vụ cụ thể     |
| **Tính tổ chức**      | Có **cấu trúc rõ ràng**, quy định cách viết mã, tổ chức dự án | Không có cấu trúc cố định, dùng linh hoạt                    |
| **Tính mở rộng**      | Dễ dàng **mở rộng, tái sử dụng**, tích hợp CI/CD           | Thường giới hạn trong khả năng đã có                         |
| **Thành phần tích hợp** | Bao gồm **thư viện, công cụ hỗ trợ, định dạng test, cấu hình...** | Thường chỉ có một **chức năng chính** duy nhất               |
| **Ví dụ**             | Playwright, Selenium, Cypress, JUnit, TestNG            | Postman (test API), Chrome DevTools, Firebug, JMeter (load test) |
---
## 4. Getting started with Playwright: Tương tác với phần tử, test hooks

### Tương tác với phần tử

- **Click**:

```js
await page.click('text=More information');
```

- **Nhập liệu**:

```js
await page.fill('input[name="q"]', 'Playwright');
```

- **Lấy text**:

```js
const text = await page.textContent('h1');
```

### Test hooks

- `beforeAll`, `afterAll`: chạy một lần trước/sau toàn bộ test.
- `beforeEach`, `afterEach`: chạy trước/sau từng test.

**Ví dụ**:

```js
test.beforeEach(async ({ page }) => {
  await page.goto('https://example.com');
});
```

---

## 5. Data Driven Test

Tạo test chạy với nhiều dữ liệu khác nhau:

```js
const testData = [
  { input: 'Playwright', expected: 'Playwright' },
  { input: 'Testing', expected: 'Testing' }
];

for (const data of testData) {
  test(`searching for ${data.input}`, async ({ page }) => {
    await page.goto('https://google.com');
    await page.fill('input[name=q]', data.input);
    await page.press('input[name=q]', 'Enter');
    await expect(page).toHaveTitle(new RegExp(data.expected));
  });
}
```

---

## 6. Tổ chức code với POM (Page Object Model), Visual Testing

### POM là gì?

Tách biệt thao tác và locator thành class riêng để dễ bảo trì.

**Ví dụ**:

```js
// pageObjects/HomePage.js
class HomePage {
  constructor(page) {
    this.page = page;
    this.searchInput = page.locator('input[name=q]');
    this.searchButton = page.locator('input[type=submit]');
  }

  async goto() {
    await this.page.goto('https://google.com');
  }

  async search(text) {
    await this.searchInput.fill(text);
    await this.searchButton.click();
  }
}

module.exports = { HomePage };
```

**Trong test**:

```js
const { HomePage } = require('./pageObjects/HomePage');

test('search test', async ({ page }) => {
  const home = new HomePage(page);
  await home.goto();
  await home.search('Playwright');
});
```

### Visual Testing

Chụp ảnh màn hình và so sánh ảnh:

```js
await expect(page).toHaveScreenshot('homepage.png');
```

So sánh ảnh để phát hiện thay đổi giao diện.

---

## 7. Configuration nâng cao, Test Generator

### Configuration nâng cao

Cấu hình `playwright.config.js`:

```js
module.exports = {
  timeout: 30000,
  use: {
    headless: true,
    viewport: { width: 1280, height: 720 },
  },
  projects: [
    { name: 'chromium', use: { browserName: 'chromium' } },
    { name: 'firefox', use: { browserName: 'firefox' } },
  ],
};
```

### Test Generator (Record Test)

Ghi lại thao tác người dùng thành mã test:

```bash
npx playwright codegen https://example.com
```

Giao diện sẽ ghi thao tác và xuất script ở định dạng JS hoặc Python.

---

## 8. API Testing với Playwright

Playwright hỗ trợ gửi request API.

**Ví dụ test API**:

```js
const { test, expect, request } = require('@playwright/test');

test('API test example', async () => {
  const apiContext = await request.newContext();
  const response = await apiContext.get('https://api.example.com/users/1');
  expect(response.status()).toBe(200);

  const data = await response.json();
  expect(data.id).toBe(1);
});
```

Có thể gửi request các phương thức: GET, POST, PUT, DELETE.

Hỗ trợ quản lý headers, cookies và kết hợp UI với API test.

---
