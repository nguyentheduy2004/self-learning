# Unit testing - Kiểm thử đơn vị

# Integration testing - Kiểm thử tích hợp

# System testing - Kiểm thử mức hệ thống

# Acceptance testing - Kiểm thử chấp nhận

![Unit Testing](image-20250506-071652.png)

## Unit testing - Kiểm thử mức đơn vị

### Định nghĩa
Một đơn vị phần mềm (Unit) là gì? Một Unit là một thành phần phần mềm nhỏ nhất mà ta kiểm tra được. Nó bao gồm các các hàm (Function), thủ tục (Procedure), lớp (Class), hoặc các phương thức (Method).

Kiểm thử đơn vị nhằm đảm bảo rằng code viết cho đơn vị đáp ứng được yêu cầu cụ thể của nó, trước khi tích hợp với các đơn vị khác.

Ngoài việc kiểm tra sự phù hợp với quy định của chương trình, kiểm thử đơn vị cũng xác minh rằng toàn bộ code đã được viết cho đơn vị có thể thực thi.

Kiểm thử đơn vị yêu cầu truy cập vào code đang được kiểm tra.

Một phương pháp tiếp cận kiểm thử đơn vị được gọi là phát triển dựa trên kiểm thử. Như tên gọi của nó, trước tiên viết các ca kiểm thử, sau đó xây dựng, kiểm thử và thay đổi code cho đến khi đơn vị vượt qua các kiểm thử. Đây là một phương pháp lặp lại cho kiểm thử đơn vị.

> **Unit testing là kiểu white box testing**

### Mục đích
- Để xác định rằng mỗi đơn vị phần mềm được thực hiện như thiết kế.
- Làm tăng sự tự tin khi thay đổi / bảo trì code.
- Phát hiện lỗi sớm giúp giảm chi phí so với lỗi phát hiện ở giai đoạn muộn như kiểm thử chấp nhận.

### Áp dụng
Sau khi code xong feature `Upload Image` cho `Custom option Image` ngoài Storefront, team dev thực hiện viết các unit test với các case:

- Tải lên các ảnh hợp lệ (.png, .jpg,...) thông báo thành công.
- Tải lên các ảnh không hợp lệ (.txt, .pds,...) thông báo lỗi.
- Đảm bảo chức năng hoạt động đúng sau khi sửa code.

---

## Integration Test – Kiểm thử tích hợp

### Định nghĩa
Kiểm thử tích hợp là cấp độ kiểm thử phần mềm trong đó các đơn vị riêng lẻ được kết hợp và thử nghiệm dưới dạng một nhóm.

Tập trung vào kiểm tra truyền dữ liệu giữa các module – tích hợp các hàm, các màn hình, hoặc các module chức năng.

### Mục đích
- Để lộ lỗi trong sự tương tác giữa các đơn vị tích hợp.
- Tìm ra lỗi khi kết nối các module.
- Sử dụng test driver và test stub để hỗ trợ kiểm thử.

### Các phương pháp tiếp cận

- **Big bang:** Tích hợp tất cả module một lần → khó xác định lỗi.
- **Top Down:** Tích hợp từ các module cha đến module con.
- **Bottom Up:** Tích hợp từ các module con đến cha.
- **Sandwich / Hybrid:** Kết hợp Top Down & Bottom Up.

> Cần lưu ý: kiểm thử tích hợp có thể gặp rủi ro ở mức kỹ thuật (đa nền tảng), vận hành (quy trình), hoặc doanh nghiệp (tác động hệ thống khác).

### Áp dụng
Với feature `Update custom option image`, các chức năng cần test tích hợp bao gồm:

- Preview ảnh, chỉnh sửa, điều chỉnh kích thước
- Thêm nút Add to Cart và guide text vào pop-up preview
- Filter đen trắng, remove background ảnh upload
- Ẩn tên đầy đủ file ảnh khi upload
- Xử lý văn bản trong ô help text

**Quy trình:**

1. Dev chia từng chức năng và code riêng.
2. Team QE tạo test plan, test case, automation test.
3. Sau unit test thành công → tích hợp phần code lại.
4. QE test theo test case, run automation để tìm lỗi.
5. Dev & QE phối hợp sửa lỗi → lặp lại kiểm thử đến khi đạt yêu cầu.

---

## System Testing – Kiểm thử mức hệ thống

### Định nghĩa
Là mức kiểm thử trên phần mềm đã hoàn chỉnh và tích hợp. Kiểm thử toàn hệ thống, cả về **chức năng** lẫn **phi chức năng**.

Khác với Integration Test ở chỗ:
- **Integration Test:** kiểm tra giao tiếp giữa các đơn vị.
- **System Test:** kiểm tra hành vi toàn hệ thống.

### Mục đích
- Đánh giá hệ thống có tuân thủ đúng yêu cầu không.
- Dùng test case & test data mô phỏng thực tế.
- Tạo đánh giá khách quan theo tài liệu yêu cầu, không phụ thuộc code.

### Áp dụng
Sau khi kiểm thử tích hợp feature `Update custom option image`, team cần:

- Test toàn bộ hệ thống trước khi build Production.
- Đảm bảo không gây lỗi cho các chức năng cũ.
- Run full test theo **release checklist** để đảm bảo toàn vẹn hệ thống.

---

## Acceptance Testing – Kiểm thử chấp nhận

### Định nghĩa
Kiểm thử mức cuối cùng để đánh giá phần mềm có phù hợp với **yêu cầu kinh doanh**, trước khi chính thức bàn giao.

- Do **người dùng cuối, PO, PM** thực hiện.
- Dùng dữ liệu thực tế để đánh giá.

### Mục đích
- Xác nhận hệ thống có sẵn sàng triển khai không.
- Kiểm tra tính đầy đủ các đặc tính chức năng/phi chức năng.
- Không tập trung tìm lỗi mà là xác nhận mức sẵn sàng.

### Các loại kiểm thử chấp nhận

- **Alpha Testing:** thực hiện nội bộ, trước khi release.
- **Beta Testing:** người dùng test tại địa điểm của họ → phản hồi thực tế.

### Áp dụng
Feature `Update custom option image` sau khi được team QA test xong sẽ:

- Giao cho PM/PO để kiểm tra nghiệm thu.
- Nếu phát hiện lỗi, yêu cầu team dev fix.
- Nếu đạt yêu cầu, thông báo đến người dùng thật và nhận phản hồi thêm để cải thiện sản phẩm.
