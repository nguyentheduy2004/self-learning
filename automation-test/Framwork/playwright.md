
# Tìm hiểu về Playwright

## 1. Tìm hiểu Playwright: Viết script cơ bản
**Khởi tạo project**:
```bash
npm init playwright@latest
```
### Viết script cơ bản

Tạo file `example.spec.js`:

```js
const { test, expect } = require('@playwright/test');

test('basic test', async ({ page }) => {
  await page.goto('https://example.com');
  const title = await page.title();
  expect(title).toBe('Example Domain');
});
```

### Chạy test

```bash
npx playwright test
```
### xem report
```bash
npx playwright show-report
```
---
## 2. Getting started with Playwright: Tương tác với phần tử, test hooks

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

## 3. Data Driven Test

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

## 4. Tổ chức code với POM (Page Object Model), Visual Testing

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

## 5. Configuration nâng cao, Test Generator

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

### Test Generator

Ghi lại thao tác người dùng thành mã test:

```bash
npx playwright codegen https://example.com
```

Giao diện sẽ ghi thao tác và xuất script ở định dạng JS hoặc Python.

---

## 6. API Testing với Playwright

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

## 7. So sánh Playwright và Selenium

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


