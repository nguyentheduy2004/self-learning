# Tìm hiểu DOM: Cấu trúc, HTML DOM và XML DOM

## 1. DOM là gì?

+ DOM (Document Object Model) là mô hình đối tượng tài liệu, đại diện cho cấu trúc nội dung của tài liệu HTML hoặc XML dưới dạng cây. DOM cho phép lập trình viên truy cập và thay đổi nội dung, cấu trúc cũng như kiểu dáng của trang web hoặc tài liệu dữ liệu thông qua JavaScript và các ngôn ngữ lập trình khác.
+ DOM là cầu nối giữa mã HTML/XML và JavaScript hoặc ngôn ngữ xử lý khác. 
---

## 2. Cấu trúc của DOM

DOM được tổ chức như một cây (tree) với các **nút (nodes)**:

- **Document**: nút gốc (root node) của tài liệu.
- **DocumentType**: nút riêng biệt để định nghĩa kiểu tài liệu HTML hay XML.
- **Element**: các thẻ HTML như `<div>`, `<p>`, `<a>`, v.v.
- **Text**: nội dung văn bản nằm trong các phần tử.
- **Attribute**: thuộc tính của phần tử, ví dụ `id`, `class`, `href`, v.v.
- **Comment**: các chú thích trong tài liệu HTML.
---
### Các Thẻ HTML Thường Gặp Trong DOM

| Thẻ HTML      | Là gì?                            | Dùng để làm gì? |
|---------------|-----------------------------------|------------------|
| `<div>`       | Container (khối chứa)              | Gom nhóm các phần tử, bố cục trang |
| `<p>`         | Paragraph (đoạn văn)               | Hiển thị văn bản dạng đoạn |
| `<a>`         | Anchor (liên kết)                  | Tạo liên kết đến URL hoặc phần tử khác |
| `<span>`      | Inline container                   | Gom nhóm nội dung inline, dùng với CSS |
| `<h1>` - `<h6>`| Heading (tiêu đề)                  | Tiêu đề các cấp độ từ lớn đến nhỏ |
| `<ul>`        | Unordered List (danh sách không thứ tự) | Liệt kê các mục có dấu chấm |
| `<ol>`        | Ordered List (danh sách có thứ tự) | Liệt kê các mục có đánh số |
| `<li>`        | List Item                          | Mục trong danh sách `<ul>` hoặc `<ol>` |
| `<table>`     | Table (bảng)                       | Tạo bảng dữ liệu |
| `<tr>`        | Table Row (hàng trong bảng)        | Đại diện cho 1 hàng |
| `<td>`        | Table Data (ô dữ liệu)             | Đại diện cho 1 ô |
| `<th>`        | Table Header (ô tiêu đề)           | Đại diện cho 1 ô tiêu đề trong bảng |
| `<form>`      | Form (biểu mẫu)                    | Thu thập dữ liệu từ người dùng |
| `<input>`     | Input field                        | Trường nhập liệu (text, radio, checkbox...) |
| `<textarea>`  | Multi-line input                   | Nhập văn bản nhiều dòng |
| `<button>`    | Nút bấm                            | Kích hoạt hành động khi click |
| `<label>`     | Nhãn                               | Gắn nhãn cho input để dễ sử dụng |
| `<select>`    | Dropdown                           | Hiển thị danh sách chọn |
| `<option>`    | Option in select                   | Mục trong dropdown |
| `<img>`       | Hình ảnh                           | Hiển thị ảnh |
| `<iframe>`    | Inline Frame                       | Nhúng trang web khác vào trang hiện tại |
| `<script>`    | Script                             | Nhúng mã JavaScript |
| `<link>`      | Link resource                      | Liên kết tới CSS hoặc tài nguyên ngoài |
| `<meta>`      | Metadata                           | Cung cấp thông tin về trang (encoding, viewport...) |
| `<header>`    | Header section                     | Phần đầu của trang hoặc khu vực |
| `<footer>`    | Footer section                     | Phần cuối của trang hoặc khu vực |
| `<nav>`       | Navigation                         | Thanh điều hướng |
| `<section>`   | Section                            | Khu vực nội dung riêng biệt |
| `<article>`   | Article                            | Bài viết hoặc khối nội dung độc lập |
| `<aside>`     | Aside content                      | Nội dung phụ, bên lề (ví dụ sidebar) |
| `<main>`      | Main content                       | Nội dung chính của trang |
---
## 3. So sánh HTML DOM và XML DOM

| Tiêu chí             | HTML DOM                                           | XML DOM                                                  |
|----------------------|----------------------------------------------------|-----------------------------------------------------------|
| **Định nghĩa**        | Mô hình đối tượng tài liệu dành cho HTML.         | Mô hình đối tượng tài liệu dành cho XML.                 |
| **Mục đích**          | Hiển thị và thao tác nội dung trang web.          | Truy xuất, phân tích và thao tác dữ liệu XML.            |
| **Tính nghiêm ngặt**  | Không nghiêm ngặt về cú pháp.                     | Rất nghiêm ngặt về cú pháp.                              |
| **Trình duyệt hỗ trợ**| Mặc định được hỗ trợ bởi trình duyệt.             | Dùng trong các ứng dụng xử lý dữ liệu hoặc web services. |
| **Namespace**         | Không sử dụng.                                    | Có hỗ trợ namespace.                                     |
| **Dữ liệu văn bản**   | Trình bày cho người dùng.                         | Trao đổi và lưu trữ dữ liệu.                             |
| **Đối tượng gốc**     | `document`                                        | `document`                                                |

---
## 4. Các mối quan hệ trong DOM
### 1. Quan hệ cha - con (Parent - Child)

Mỗi nút (node) có thể có cha (parent node) và nhiều con (child nodes).

**Ví dụ:**

```html
<div>  <!-- cha -->
  <p>Đoạn văn</p>  <!-- con -->
  <a href="#">Link</a> <!-- con -->
</div>
```

Ở đây, `<div>` là cha của `<p>` và `<a>`, còn `<p>` và `<a>` là con của `<div>`.

---

### 2. Quan hệ anh chị em (Sibling)

Các nút con có cùng cha gọi là anh chị em (siblings).

**Ví dụ:** `<p>` và `<a>` trong ví dụ trên là anh chị em với nhau.

---

### 3. Quan hệ ông cố nội - cháu (Ancestor - Descendant)

Một nút gọi là **ông cố nội** (ancestor) nếu nằm ở cấp trên trong cây DOM so với nút khác, tức là cha, ông, cụ,... của nút đó.

Nút gọi là **cháu** (descendant) nếu nằm ở cấp dưới trong cây so với nút khác.

**Ví dụ:**

```html
<body>
  <div>
    <p>Text</p>
  </div>
</body>
```

`<body>` là ông cố nội của `<p>`,  
`<p>` là cháu của `<body>`.

---

### 4. Quan hệ anh chị em trước - sau (Preceding-sibling & Following-sibling)

Với các nút anh chị em, có thể xác định nút đứng trước (`previousSibling`) hoặc đứng sau (`nextSibling`).

**Ví dụ:**

```html
<ul>
  <li>Item 1</li>   <!-- Anh/chị em đứng trước -->
  <li>Item 2</li>   <!-- Phần tử hiện tại -->
  <li>Item 3</li>   <!-- Anh/chị em đứng sau -->
</ul>
```

---

### 5. Quan hệ gốc - nút (Root - Node)

Nút `Document` là **gốc** (root) của toàn bộ cây DOM.

Mọi nút khác đều là **con** (trực tiếp hoặc gián tiếp) của nút gốc này.

---

### 6.Quan hệ anh chị em trước - sau (Preceding & Following)
#### 1. Following
+ Chọn tất cả các phần tử nằm sau phần tử hiện tại trong cây DOM, theo thứ tự xuất hiện trong tài liệu.
+ Bao gồm tất cả các phần tử nằm sau phần tử hiện tại, không phân biệt cấp bậc hay vị trí.
+ Chọn cả anh/chị em, con cháu, chú bác,... miễn là xuất hiện sau phần tử đó theo thứ tự DOM.
```html
<div>
  <p id="p1">Paragraph 1</p>       <!-- Phần tử hiện tại -->
  <span>Span 1</span>              <!-- following -->
  <p>Paragraph 2</p>               <!-- following -->
  <div>
    <p>Paragraph 3</p>             <!-- following (con cháu bên trong div) -->
  </div>
</div>
```
```xpath
//p[@id='p1']/following::p 
```
Kết quả: chọn 2 thẻ có nội dung "Paragraph 2" và "Paragraph 3".
#### 2. Preceding
+ Chọn tất cả các phần tử nằm trước phần tử hiện tại trong cây DOM, theo thứ tự xuất hiện trong tài liệu.
+ Bao gồm tất cả các phần tử nằm trước phần tử hiện tại, không phân biệt cấp bậc.
+ Có thể là anh/chị em, cha mẹ, chú bác,... miễn là xuất hiện trước phần tử đó theo thứ tự DOM.
```html
<div>
  <p>Paragraph -1</p>             <!-- preceding -->
  <p>Paragraph 0</p>              <!-- preceding -->
  <div>
    <p id="p2">Paragraph 1</p>    <!-- Phần tử hiện tại -->
  </div>
  <span>Span 1</span>             <!-- following -->
</div>
```
```xpath
//p[@id='p2']/preceding::p 
```
Kết quả: chọn 2 thẻ có nội dung "Paragraph 0" và "Paragraph -1".