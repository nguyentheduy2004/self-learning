
# 📘 TỔNG QUAN VỀ API VÀ API TESTING

---

## Phần I: API

### 1.1. API là gì?

** Khái niệm:**

> **API (Application Programming Interface)** – Giao diện lập trình ứng dụng là một tập hợp các quy tắc, giao thức và công cụ cho phép các phần mềm hoặc hệ thống khác nhau tương tác và giao tiếp với nhau.

** Ví dụ (mua hàng onl):**

- Bạn là **khách hàng** muốn mua một chiếc áo.
- Bạn không đến trực tiếp **kho hàng (server)** để lấy áo → bạn sử dụng **ứng dụng mua sắm (API)**.
- Ứng dụng sẽ gửi yêu cầu đến kho, kho kiểm tra hàng, đóng gói, và giao hàng cho bạn  → Bạn chỉ thấy kết quả **áo được giao đến**.
- Bạn không cần biết hệ thống ra sao .

** Vai trò API:**

- Là **trung gian** giữa Client (người dùng, ứng dụng) và Server (dữ liệu, xử lý).
- API định nghĩa rõ cách tương tác, dữ liệu gửi/nhận, và quyền truy cập.

---

### 1.2. Tại sao API quan trọng? 

| Lợi ích | Mô tả |
|--------|-------|
|  Tái sử dụng | Một chức năng được xây dựng 1 lần, dùng được nhiều nơi. VD: Đăng nhập Google. |
|  Dễ tích hợp | Dễ dàng kết nối các hệ thống khác nhau, bất kể nền tảng hay ngôn ngữ. |
|  Phát triển độc lập | Mỗi nhóm có thể làm module riêng, miễn tuân theo API. |
|  Tự động hóa | API giúp máy móc, hệ thống tự động thao tác. |
|  Bảo mật | Kiểm soát dữ liệu & quyền truy cập theo chính sách. |
|  Mô hình kinh doanh | Cung cấp API như sản phẩm: Google Maps API, Zalo API... |

---

### 1.3. Cơ chế hoạt động API - Request/Response 

**Mô hình Client-Server:**

```text
Client ----(HTTP Request)----> API Gateway/Server---(HTTP Response)----->Client

```

**Cấu trúc HTTP Request:**

- **Endpoint (URL):** `/products/123`
- **HTTP Method:**
  - `GET`: Lấy dữ liệu.
  - `POST`: Tạo mới.
  - `PUT`: Cập nhật toàn bộ.
  - `PATCH`: Cập nhật 1 phần.
  - `DELETE`: Xóa.

- **Headers:** Metadata của request
  - `Content-Type: application/json`
  - `Authorization: Bearer <token>`
  - `Accept: application/json`

- **Body:** Dữ liệu gửi lên, thường dạng JSON:
  ```json
  {
    "name": "New Product",
    "price": 100
  }
  ```

**HTTP Response:**

- **Status Code:**
  - 2xx (Success): `200 OK`, `201 Created`
  - 3xx (Redirection): `301 Moved Permanently`
  - 4xx (Client Error):`400 Bad Request`, `401 Unauthorized`, `404 Not Found`
  - 5xx (Server Error):`500 Internal Server Error`

- **Headers:**
  - `Content-Type`, `Content-Length`

- **Body:**
  ```json
  {
    "id": 123,
    "name": "Product A",
    "price": 50
  }
  ```

---

### 1.4. Các loại API phổ biến

| Loại | Mô tả |
|------|-------|
| **REST** | Phổ biến nhất, dùng HTTP method, dữ liệu thường là JSON. |
| **SOAP** | Cấu trúc XML nghiêm ngặt, dùng trong các hệ thống lớn, ngân hàng, doanh nghiệp. |
| **GraphQL** | Truy vấn chính xác dữ liệu cần. Giảm dư thừa. Hiện đại, linh hoạt hơn REST. |

---

## Phần II: Authentication & Authorization

### 2.1. Sự khác biệt giữa Authentication và Authorization

| Khía cạnh | Authentication (Xác thực) | Authorization (Phân quyền) |
|----------|----------------------------|-----------------------------|
| Câu hỏi | "Bạn là ai?" | "Bạn được làm gì?" |
| Mục tiêu | Xác minh danh tính | Cấp quyền truy cập |
| Diễn ra khi | Đầu tiên | Sau khi xác thực xong |
| Ví dụ | Đăng nhập | Chỉ admin mới được xóa tài khoản |

---

### 2.2. Các cơ chế Authentication phổ biến

| Loại | Mô tả | Ưu & Nhược |
|------|------|-------------|
| **Basic Auth** | Gửi `username:password` mã hóa Base64 trong Header. | Đơn giản, nhưng không an toàn nếu không có HTTPS. |
| **API Key** | Gửi 1 chuỗi key định danh trong Header hoặc URL. | Dễ triển khai, dùng cho xác thực ứng dụng. |
| **Bearer Token (OAuth 2.0)** | Client lấy `access_token`, gửi vào Header mỗi lần gọi. | Bảo mật cao, phổ biến cho app hiện đại. |
| **Session-based (Cookie)** | Server tạo session, gửi `SessionID` về Client lưu bằng Cookie. | Dùng nhiều cho web truyền thống. |

---

### 2.3. Authorization: Phân quyền truy cập

| Mô hình | Mô tả |
|--------|-------|
| **RBAC (Role-Based)** | Gán quyền theo vai trò: admin, user, editor. |
| **ABAC (Attribute-Based)** | Dựa trên thuộc tính người dùng, hành vi, thời gian, địa điểm... |

**🔎 Kiểm thử Authorization cần:**
- User A không thấy dữ liệu User B.
- Không có quyền thì bị từ chối truy cập.
- Gán sai vai trò → kiểm tra giới hạn hành vi.

---

### 2.4. Rủi ro nếu làm sai Auth/Author

- Rò rỉ dữ liệu.
- Truy cập trái phép tài nguyên.
- OWASP API Top 10:
  - BOLA (Broken Object Level Authorization)
  - Broken Authentication
  - Broken Function Level Authorization

---

## Phần III: API Testing

### 3.1. API Testing là gì?

> Là quá trình kiểm thử API bằng cách gửi các request (GET, POST...) và kiểm tra response mà không cần thông qua giao diện UI.

---

### 3.2. Vì sao phải test API?

- Phát hiện lỗi sớm ở tầng logic.
- Tốc độ nhanh hơn UI testing.
- Dễ tự động hóa & tích hợp CI/CD.
- Ổn định hơn UI testing (ít thay đổi).
- Không phụ thuộc nền tảng.
- Bao phủ nhiều logic hơn giao diện có thể thể hiện.

---

### 3.3. Kiểm thử API gồm những gì?

| Tiêu chí | Mô tả |
|---------|------|
| Dữ liệu trả về | Có đúng định dạng, giá trị, schema không? |
| Status Code | Có phản ánh đúng kết quả request không? |
| Hiệu suất | Phản hồi có đủ nhanh không? |
| Xử lý lỗi | Có xử lý hợp lệ các input sai, server lỗi? |
| Bảo mật | Có kiểm tra Auth & Author đúng không? |
| Tính nhất quán | Gọi nhiều lần có cho kết quả giống nhau? |

---

## Phần IV: Các loại hình và quy trình kiểm thử API

### 4.1. Các loại kiểm thử API

| Loại | Mục tiêu |
|------|---------|
| **Functional Testing** | Kiểm tra đúng/sai của chức năng API (đúng data, đúng method, sai input...). |
| **Performance Testing** | Kiểm tra tốc độ phản hồi, khả năng chịu tải (stress, load test). |
| **Security Testing** | Kiểm tra xác thực, phân quyền, SQL injection, brute-force, DDoS... |
| **Reliability Testing** | API có hoạt động ổn định lâu dài không? |
| **Usability & Documentation Testing** | Kiểm thử khả năng sử dụng của API. |

---

## Checklist kiểm thử API cơ bản

- [1] Gửi request hợp lệ → Kiểm tra response đúng.
- [2] Gửi request thiếu/sai field → Xử lý lỗi đúng.
- [3] Check status code đúng mục đích.
- [4] Test với token hợp lệ, hết hạn, sai, thiếu.
- [5] Test role user không được thực hiện hành động admin.
- [6] Test performance: thời gian phản hồi < x ms.
- [7] Test nhiều request đồng thời (load test).
- [8] Kiểm tra format response JSON (schema).
- [9] Test dữ liệu biên (max, min, null...).

---

## Công cụ hỗ trợ kiểm thử API

| Công cụ | Mục đích |
|--------|----------|
| **Postman** | Giao diện thân thiện để test API thủ công, tạo collection test. |
| **Swagger UI** | Test trực tiếp trên giao diện tài liệu API. |
| **JMeter** | Performance & Load Test. |
| **RestAssured (Java)** | Tự động hóa API test. |

---

