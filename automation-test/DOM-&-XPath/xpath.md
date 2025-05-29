
# Tìm hiểu XPath

## 1. XPath là gì?
XPath là viết tắt của **XML Path** — một ngôn ngữ dùng để định vị và tìm kiếm các phần tử trên tài liệu XML hoặc HTML.  
Nó cho phép bạn tìm kiếm phần tử trên trang web dựa vào cấu trúc DOM và cú pháp XML.

---

## 2. Test XPath như thế nào?
1. Mở trình duyệt Chrome.
2. Bấm `F12` hoặc chuột phải chọn **Inspect** để mở DevTools.
3. Chọn tab **Elements**.
4. Bấm `Ctrl + F`.
5. Nhập XPath vào ô tìm kiếm — Chrome sẽ highlight phần tử tương ứng nếu có.

---

## 3. Cú pháp XPath

```xpath
<loại_xpath><tagname>[<@attribute>=<value>]
<loại_xpath><tagname>[<method>]
```
- `<loại_xpath>`:  
  - `/` → XPath tuyệt đối  
  - `//` → XPath tương đối 
  - `//*` → Chọn tất cả các phần tử trong DOM.

- `<tagname>`: Tên thẻ HTML (ví dụ: `div`, `input`, `li`, ...)
- `[@attribute=value]`: Điều kiện tìm kiếm theo thuộc tính
- `[method]`: Hàm XPath như `contains()`, `text()`, `position()`...
- `.`: Đại diện cho node hiện tại.
- `..`: Đại diện cho node cha.
---
#### Các Hàm XPath Thường Dùng `[method]`

| Hàm XPath         | Mô tả chức năng                          | Ví dụ sử dụng                            | Giải thích |
|-------------------|-------------------------------------------|------------------------------------------|------------|
| `text()`          | Lấy nội dung văn bản của node             | `//p[text()='Xin chào']`                 | Chọn thẻ `<p>` có nội dung là "Xin chào" |
| `contains()`      | Kiểm tra node có chứa chuỗi con          | `//a[contains(@href, 'google')]`         | Chọn thẻ `<a>` có `href` chứa "google" |
| `starts-with()`   | Kiểm tra node bắt đầu bằng chuỗi         | `//div[starts-with(@id, 'user_')]`       | Chọn `<div>` có id bắt đầu bằng `user_` |
| `ends-with()`     | Kiểm tra node kết thúc bằng chuỗi (XPath 2.0+) | `//div[ends-with(@class, '_item')]` | Chọn class kết thúc bằng `_item` |
| `position()`      | Lấy vị trí của node trong tập kết quả    | `//li[position()=1]`                     | Chọn phần tử `<li>` đầu tiên |
| `last()`          | Chọn phần tử cuối cùng                   | `//tr[last()]`                           | Lấy dòng cuối cùng của bảng |
| `not()`           | Điều kiện phủ định                       | `//input[not(@type='hidden')]`           | Chọn `<input>` không có type là hidden |
| `name()`          | Trả về tên của node                      | `//*[name()='input']`                    | Chọn tất cả node có tên là `input` |
| `count()`         | Đếm số lượng node                        | `count(//div)`                           | Trả về số lượng thẻ `<div>` |
| `string-length()` | Độ dài chuỗi                             | `//*[string-length(text()) > 10]`        | Chọn node có nội dung dài hơn 10 ký tự |
| `normalize-space()` | Xóa khoảng trắng đầu/cuối và chuẩn hóa | `//p[normalize-space()='Hello']`         | So sánh chuỗi sau khi loại bỏ khoảng trắng thừa |
| `substring()`     | Cắt chuỗi con                            | `substring('OpenAI', 1, 4)` → `"Open"`   | Trích xuất chuỗi con từ chuỗi |
| `substring-before()` | Cắt chuỗi trước ký tự                 | `substring-before('a@b.com', '@')` → `"a"` | Lấy phần trước ký tự `@` |
| `substring-after()`  | Cắt chuỗi sau ký tự                   | `substring-after('a@b.com', '@')` → `"b.com"` | Lấy phần sau ký tự `@` |
| `translate()`     | Thay thế ký tự                           | `translate('XPath', 'XP', 'xp')` → `"xpath"` | Chuyển chữ hoa thành chữ thường |
| `boolean()`       | Ép kiểu boolean                          | `boolean(//div[@class='error'])`         | Trả về `true` nếu có thẻ `<div class="error">` |
| `true()` / `false()` | Giá trị boolean                       | `//*[@checked='true']`                   | Kiểm tra boolean đúng/sai |

---
## 4. Các loại XPath

| Loại XPath  | Cách bắt đầu | Đặc điểm | Ví dụ |
|-------------|---------------|----------|----------|
| Tuyệt đối   | `/`           | Tìm đường dẫn chính xác từ gốc đến phần tử |/html/body/div/div/div/h2|
| Tương đối   | `//`          | Tìm kiếm tương đối, tìm mọi node phù hợp trong DOM |//h2[@class='header']|

Nên dùng XPath tương đối (//) trong hầu hết các trường hợp vì:
- Không bị phụ thuộc vào toàn bộ cây DOM.
- Dễ bảo trì khi cấu trúc trang web thay đổi.
- Dễ kết hợp với các hàm như contains(), text(), starts-with(),...
- Không nên dùng XPath tuyệt đối (/) vì dễ bị lỗi khi giao diện của web thay đổi
---

## 5. Ví dụ XPath cơ bản

Giả sử có HTML:

```html
<div>
  <ul id="menu">
    <li class="item">Trang chủ</li>
    <li class="item selected">Giới thiệu</li>
    <li class="item">Liên hệ</li>
  </ul>
</div>
```

Ví dụ XPath:

```xpath
//ul[@id='menu'] 
→ Tìm thẻ <ul> có id="menu"

///li[@class='item selected']
→ Tìm thẻ <li> có class="item selected"

//ul[@id='menu']/li[2]
→ Tìm thẻ <li> thứ 2 trong ul, kết quả: "Giới thiệu"

//li[contains(@class, 'item')]
→ Tìm tất cả li có class chứa từ "item"

//li[text()='Liên hệ']
→ Tìm li có nội dung đúng là "Liên hệ"
```

## 6. XPath Axes Method – Tìm phần tử động không theo thứ tự cố định

Dùng để tìm phần tử dựa vào **quan hệ vị trí trong DOM** (cha, con, anh em...).

| Phương thức (Axis)      | Ý nghĩa                  | Ví dụ XPath                                      | Giải thích                                                |
|-------------------------|--------------------------|-------------------------------------------------|-----------------------------------------------------------|
| `following`             | Các phần tử phía sau, trừ phần tử con của node đó| `//*[@type="text"]//following::input[1]`        | Tìm input đầu tiên sau thẻ có `type="text"`               |
| `ancestor`              | Phần tử tổ tiên          | `//*[@type="password"]//ancestor::div`           | Tìm các thẻ div là tổ tiên của phần tử có type password   |
| `child`                 | Phần tử con trực tiếp    | `//*[@id='java_technology']//child::li`          | Tìm các thẻ `<li>` là con trực tiếp của thẻ có id        |
| `preceding`             | Các phần tử trước trừ các node trực hệ của phần tử đó| `//*[@type="submit"]//preceding::input`          | Tìm tất cả thẻ `<input>` đứng trước phần tử có type submit |
| `following-sibling`     | Anh/chị em cùng cấp sau  | `//*[@type="submit"]//following-sibling::input` | Tìm các thẻ `<input>` cùng cấp nằm sau phần tử có type submit |
| `preceding-sibling`     | Anh/chị em cùng cấp trước| `//li[@id='target']/preceding-sibling::li`       | Tìm các thẻ `<li>` cùng cấp đứng trước thẻ `<li id="target">` |
| `parent`                | Phần tử cha              | `//*[@id="rt-feature"]//parent::div[1]`          | Tìm thẻ `<div>` là cha trực tiếp của phần tử có id        |
| `self`                  | Chính nó                 | `descendant-or-self::node()`                      | Kết hợp tìm chính nó và tất cả các hậu duệ                 |
| `descendant`            | Hậu duệ                  | `//*[@id='rt-feature']//descendant::a[1]`         | Tìm thẻ `<a>` đầu tiên là hậu duệ của phần tử có id        |


---

### Ví dụ thực tế
## Ví dụ 1: `ancestor` – Tìm tổ tiên (cha, ông...)

### HTML:
```html
<div class="login-form">
  <form>
    <label for="username">Tên đăng nhập</label>
    <input type="text" id="username" />
  </form>
</div>
```

### XPath:
```xpath
//input[@id='username']//ancestor::div
```

**Giải thích**: Tìm thẻ `<div>` là tổ tiên của `<input id='username'>`.

---

## Ví dụ 2: `following-sibling` – Tìm phần tử ngang cấp đứng sau

### HTML:
```html
<ul>
  <li>Trang chủ</li>
  <li class="active">Giới thiệu</li>
  <li>Liên hệ</li>
</ul>
```

### XPath:
```xpath
//li[text()='Giới thiệu']//following-sibling::li
```

**Giải thích**: Tìm các `<li>` ngang cấp đứng **sau** phần tử có text `"Giới thiệu"`.

---

## Ví dụ 3: `preceding` – Tìm phần tử bất kỳ đứng trước

### HTML:
```html
<h2>Tiêu đề</h2>
<p>Mô tả đoạn văn...</p>
<input type="submit" value="Gửi" />
```

### XPath:
```xpath
//input[@type='submit']//preceding::h2
```

**Giải thích**: Tìm tất cả các phần tử `<h2>` đứng **trước** nút submit.

---

## Ví dụ 4: `child` – Tìm con trực tiếp

### HTML:
```html
<ul id="menu">
  <li>Trang chủ</li>
  <li>Giới thiệu</li>
</ul>
```

### XPath:
```xpath
//ul[@id='menu']//child::li
```

**Giải thích**: Tìm tất cả `<li>` là **con trực tiếp** của `<ul id="menu">`.

---

## Ví dụ 5: `descendant` – Tìm hậu duệ (con, cháu...)

### HTML:
```html
<div id="container">
  <section>
    <article>
      <p>Đây là một đoạn văn.</p>
    </article>
  </section>
</div>
```

### XPath:
```xpath
//div[@id='container']//descendant::p
```

**Giải thích**: Tìm thẻ `<p>` là **hậu duệ** của `<div id='container'>`.

---

## Ví dụ 6: `self` – Chính nó

### HTML:
```html
<input type="text" name="email" />
```

### XPath:
```xpath
//input[@name='email']//self::input
```

**Giải thích**: Trả lại chính thẻ `<input>` (ít dùng riêng lẻ, thường dùng kết hợp).

