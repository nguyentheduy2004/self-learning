# Tìm hiểu DOM: Cấu trúc, HTML DOM và XML DOM

## 1. DOM là gì?

+ DOM (Document Object Model) là mô hình đối tượng tài liệu, đại diện cho cấu trúc nội dung của tài liệu HTML hoặc XML dưới dạng cây. DOM cho phép lập trình viên truy cập và thay đổi nội dung, cấu trúc cũng như kiểu dáng của trang web hoặc tài liệu dữ liệu thông qua JavaScript và các ngôn ngữ lập trình khác.
+ DOM là cầu nối giữa mã HTML/XML và JavaScript hoặc ngôn ngữ xử lý khác. 
---

## 2. Cấu trúc của DOM

DOM được tổ chức như một cây (tree) với các **nút (nodes)**:

- **Document**: nút gốc (root node) của tài liệu.
- **Element**: các thẻ HTML như `<div>`, `<p>`, `<a>`, v.v.
- **Text**: nội dung văn bản nằm trong các phần tử.
- **Attribute**: thuộc tính của phần tử, ví dụ `id`, `class`, `href`, v.v.
- **Comment**: các chú thích trong tài liệu HTML.

Ví dụ: đoạn HTML sau:

```html
<html>
  <body>
    <h1 id="title">hihihihiiihihihihiii!</h1>
    <p class="intro">Đoạn văn.</p>
  </body>
</html>
```

Cấu trúc DOM tương ứng:

```
Document
 └── html
     └── body
         ├── h1#title
         │    └── "hihihihiiihihihihiii!"
         └── p.intro
              └── "Đoạn văn"
```

---

## 3. HTML DOM

### 3.1 Truy cập phần tử DOM bằng JavaScript

#### Truy cập theo ID

```javascript
const title = document.getElementById("title");
```

#### Truy cập theo class

```javascript
const introParagraphs = document.getElementsByClassName("intro");
```

#### Truy cập theo tên thẻ

```javascript
const paragraphs = document.getElementsByTagName("p");
```

#### Truy cập bằng CSS selector

```javascript
const firstIntro = document.querySelector(".intro");
const allIntro = document.querySelectorAll(".intro");
```

### 3.2 Thao tác với phần tử DOM

#### Thay đổi nội dung

```javascript
title.textContent = "HiiiiiiHiiiiii";
```

#### Thay đổi thuộc tính

```javascript
title.setAttribute("style", "color: blue;");
```

#### Thêm hoặc xóa class

```javascript
title.classList.add("highlight");
title.classList.remove("highlight");
```

#### Tạo và thêm phần tử mới

```javascript
const newPara = document.createElement("p");
newPara.textContent = "Nguyễn Thế DuyDuy";
document.body.appendChild(newPara);
```

---

## 4. XML DOM

### Ví dụ tài liệu XML

```xml
<books>
  <book>
    <title>JavaScript Cơ bản</title>
    <author>Nguyễn Văn A</author>
  </book>
  <book>
    <title>JavaScript </title>
    <author>Nguyễn Văn B</author>
  </book>
</books>
```

### Xử lý bằng JavaScript

```javascript
const parser = new DOMParser();
const xmlDoc = parser.parseFromString(xmlString, "text/xml");

// Lấy danh sách các thẻ <book>
const books = xmlDoc.getElementsByTagName("book");

// Lấy tiêu đề của quyển đầu tiên
const firstTitle = books[0].getElementsByTagName("title")[0].textContent;

// Lấy thuộc tính id của sách
const bookId = books[0].getAttribute("id");

// Duyệt toàn bộ danh sách sách
for (let i = 0; i < books.length; i++) {
  const title = books[i].getElementsByTagName("title")[0].textContent;
  const author = books[i].getElementsByTagName("author")[0].textContent;
  console.log(`Sách: ${title}, Tác giả: ${author}`);
}
```

---

## 5. So sánh HTML DOM và XML DOM

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

