# 1. White Box Testing

## Khái niệm

White Box Testing là loại kiểm thử mà người kiểm thử có đầy đủ hiểu biết về mã nguồn, cấu trúc bên trong, và cách hoạt động của phần mềm. Người kiểm thử kiểm tra logic, luồng xử lý, và các thành phần mã nguồn để đảm bảo chúng hoạt động đúng.

## Đặc điểm

- Yêu cầu người kiểm thử có kiến thức lập trình và hiểu rõ mã nguồn.
- Tập trung vào kiểm tra từng đoạn mã, hàm, hoặc module.
- Thường được thực hiện ở giai đoạn kiểm thử đơn vị (Unit Testing) hoặc kiểm thử tích hợp (Integration Testing).
- Các công cụ hỗ trợ như trình gỡ lỗi (debugger) có thể được sử dụng, nhưng thao tác kiểm thử vẫn là thủ công.

## Ưu điểm

- Phát hiện lỗi sâu trong mã nguồn: Có thể tìm ra lỗi logic hoặc lỗi trong thuật toán.
- Tối ưu hóa mã: Giúp phát hiện các đoạn mã dư thừa hoặc không hiệu quả.
- Độ bao phủ cao: Có thể kiểm tra hầu hết các nhánh (branches) và luồng xử lý trong mã.

## Nhược điểm

- Yêu cầu kỹ năng cao: Người kiểm thử cần biết lập trình và hiểu cấu trúc mã.
- Tốn thời gian: Kiểm tra từng đoạn mã chi tiết mất nhiều công sức.
- Phụ thuộc vào mã nguồn: Nếu mã nguồn không được tài liệu hóa tốt, việc kiểm thử sẽ khó khăn.

## Trường hợp áp dụng

- Kiểm thử đơn vị bởi các lập trình viên trong quá trình phát triển.
- Kiểm thử các hệ thống phức tạp như phần mềm tài chính, nơi logic xử lý cần được kiểm tra kỹ lưỡng.
- Kiểm tra bảo mật để tìm lỗ hổng trong mã nguồn.

---

# 2. Black Box Testing

## Khái niệm

Black Box Testing là loại kiểm thử mà người kiểm thử không cần biết về mã nguồn hoặc cấu trúc bên trong của phần mềm. Họ chỉ tập trung vào đầu vào và đầu ra, kiểm tra xem phần mềm có đáp ứng yêu cầu chức năng và phi chức năng hay không.

## Đặc điểm

- Không yêu cầu kiến thức lập trình, phù hợp với kiểm thử viên không có nền tảng kỹ thuật.
- Tập trung vào giao diện người dùng, chức năng, và trải nghiệm người dùng.
- Thường được thực hiện ở các giai đoạn kiểm thử hệ thống (System Testing) và kiểm thử chấp nhận (Acceptance Testing).
- Dựa trên tài liệu yêu cầu (SRS) hoặc kịch bản sử dụng (Use Case).

## Ưu điểm

- Dễ thực hiện: Không cần hiểu mã nguồn, phù hợp với nhiều đối tượng kiểm thử.
- Góc nhìn người dùng: Đánh giá phần mềm từ quan điểm của người dùng cuối.
- Độc lập với mã nguồn: Không bị ảnh hưởng bởi cách phần mềm được lập trình.

## Nhược điểm

- Độ bao phủ thấp: Không kiểm tra được các lỗi sâu trong mã nguồn.
- Phụ thuộc vào tài liệu yêu cầu: Nếu yêu cầu không rõ ràng, kiểm thử có thể thiếu sót.
- Khó kiểm tra các trường hợp phức tạp: Các lỗi liên quan đến logic nội bộ có thể bị bỏ qua.

---

## Kỹ năng kiểm thử trong Black Box Testing

### Phân tích giá trị biên (Boundary Value Analysis - BVA)

- **Lý thuyết**: Kiểm tra các giá trị ở ranh giới hoặc gần ranh giới của miền đầu vào.
- **Ví dụ**: Trường tuổi chấp nhận giá trị từ 18 đến 65  
  → Kiểm thử: 17, 18, 19, 64, 65, 66  
  → Phát hiện lỗi khi nhập tuổi 66 vẫn được chấp nhận

### Phân vùng tương đương (Equivalence Partitioning)

- **Lý thuyết**: Chia miền đầu vào thành các nhóm xử lý tương tự.
- **Ví dụ**: Trường số lượng vé chấp nhận từ 1 đến 10  
  → Giá trị kiểm thử: -1, 5, 11  
  → Phát hiện lỗi khi nhập -1 không hiển thị thông báo lỗi

### Kiểm thử bảng quyết định (Decision Table Testing)

- **Lý thuyết**: Sử dụng bảng liệt kê các điều kiện và kết quả tương ứng.
- **Ví dụ**: Đăng nhập với tổ hợp tài khoản/mật khẩu đúng-sai  
  → Phát hiện lỗi thông báo không rõ ràng
  
| Điều kiện       | Quy tắc 1 | Quy tắc 2 | Quy tắc 3 | Quy tắc 4 |
|-----------------|-----------|-----------|-----------|-----------|
| **Email (T/F)** | T         | T         | F         | F         |
| **Mật khẩu (T/F)** | T         | F         | T         | F         |
| **Kết quả (E/H)** | H         | E         | E         | E         |

### Kiểm thử luồng trạng thái (State Transition Testing)

- **Lý thuyết**: Kiểm tra trạng thái hệ thống và chuyển tiếp giữa chúng.
- **Ví dụ**: Trạng thái đơn hàng: Đặt hàng → Xác nhận → Giao hàng → Hoàn thành  
  → Phát hiện lỗi khi bỏ qua bước "Xác nhận"

### Kiểm thử trường hợp sử dụng (Use Case Testing)

- **Lý thuyết**: Dựa trên tài liệu Use Case mô phỏng hành vi người dùng.
- **Ví dụ**: Kịch bản đặt vé xe → phát hiện lỗi khi không có chuyến vẫn không hiển thị thông báo

### Kiểm thử khám phá (Exploratory Testing)

- **Lý thuyết**: Kiểm thử tự do, không theo kịch bản cố định.
- **Ví dụ**: Nhập ký tự Unicode gây crash ứng dụng chat

---

## Trường hợp áp dụng

- Kiểm thử chức năng (Functional Testing) như giao diện, biểu mẫu
- Kiểm thử trải nghiệm người dùng (Usability Testing)
- Kiểm thử chấp nhận (Acceptance Testing)

---

## Ví dụ minh họa

Kiểm thử chức năng đăng nhập của website:

- **Phân vùng tương đương**: email hợp lệ, không hợp lệ, trống
- **Giá trị biên**: mật khẩu độ dài 6–20 ký tự và vượt giới hạn
- **Bảng quyết định**: tổ hợp email/mật khẩu đúng-sai
- **Khám phá**: nhập chuỗi dài/đặc biệt

> Phát hiện lỗi:  
> - Email không hợp lệ vẫn được chấp nhận  
> - Mật khẩu dài gây lỗi giao diện

---

# 3. Grey Box Testing

## Khái niệm

Grey Box Testing là sự kết hợp giữa White Box và Black Box Testing. Người kiểm thử có một phần hiểu biết về mã nguồn hoặc cấu trúc bên trong, nhưng chủ yếu kiểm tra dựa trên chức năng và giao diện, giống Black Box.

## Đặc điểm

- Yêu cầu kiến thức cơ bản về lập trình và hệ thống.
- Tập trung vào kiểm tra tích hợp hoặc các trường hợp kiểm thử phức tạp.
- Thường sử dụng các công cụ để truy cập cơ sở dữ liệu hoặc log hệ thống, nhưng thao tác kiểm thử vẫn là thủ công.

## Ưu điểm

- Kết hợp ưu điểm của cả hai: Có thể kiểm tra cả chức năng và một số khía cạnh nội bộ.
- Hiệu quả hơn Black Box: Hiểu biết về hệ thống giúp thiết kế các trường hợp kiểm thử tốt hơn.
- Phù hợp với kiểm thử tích hợp: Kiểm tra sự tương tác giữa các module hoặc hệ thống.

## Nhược điểm

- Hạn chế về độ sâu: Không kiểm tra được toàn bộ mã nguồn như White Box.
- Yêu cầu kiến thức kỹ thuật: Người kiểm thử cần hiểu một phần về hệ thống.
- Phụ thuộc vào tài liệu: Cần tài liệu về cấu trúc hệ thống để kiểm thử hiệu quả.

---

## Kỹ năng kiểm thử

- Kiểm tra cơ sở dữ liệu: Sử dụng truy vấn SQL để kiểm tra dữ liệu đầu vào/đầu ra.
- Kiểm tra API: Kiểm tra các yêu cầu và phản hồi của API bằng công cụ như Postman.
- Kiểm tra log hệ thống: Phân tích log để tìm nguyên nhân lỗi.

## Trường hợp áp dụng

- Kiểm thử tích hợp giữa các module hoặc hệ thống.
- Kiểm thử bảo mật để tìm lỗ hổng dựa trên một phần mã nguồn.
- Kiểm thử các ứng dụng web hoặc di động, nơi cần kiểm tra cả giao diện và dữ liệu phía sau.

## Ví dụ minh họa

Chức năng tải tệp lên:

- **Black Box**: Tệp PDF 5MB, 10MB, 11MB, tệp JPG  
  → Mong đợi: tệp >10MB hoặc sai định dạng bị từ chối

- **Grey Box**: Dùng SQL kiểm tra tệp đã lưu đúng chưa

- **Khám phá**: Tệp tên có ký tự đặc biệt → lỗi khi lưu vào DB

---

# So sánh White Box, Black Box, và Grey Box Testing

| Tiêu chí              | White Box     | Black Box      | Grey Box             |
|----------------------|---------------|----------------|----------------------|
| Hiểu biết mã nguồn   | Đầy đủ        | Không cần      | Một phần             |
| Mục tiêu             | Logic, mã nguồn | Chức năng, UI | Chức năng + nội bộ   |
| Kỹ năng yêu cầu      | Lập trình     | Không cần      | Kỹ thuật cơ bản      |
| Giai đoạn áp dụng    | Unit, Integration | System, Acceptance | Integration, Security |
| Độ bao phủ           | Cao           | Thấp           | Trung bình           |
| Ví dụ                | Hàm tính giá vé | Giao diện login | Tải file + kiểm tra DB |

---

## Kết luận

- **White Box Testing**: Phù hợp kiểm tra logic code, yêu cầu lập trình viên có kỹ năng chuyên môn cao.  
- **Black Box Testing**: Phù hợp kiểm thử chức năng và UX, dùng nhiều kỹ thuật thiết kế test case hiệu quả.  
- **Grey Box Testing**: Kết hợp ưu điểm của hai loại trên, phù hợp khi cần hiểu một phần hệ thống.
