
# Functional Testing

Tập trung vào việc kiểm tra xem phần mềm hoạt động như thế nào dưới góc độ của yêu cầu chức năng.

Function testing được dựa trên các chức năng, các tài liệu đặc tả hoặc sự hiểu biết của tester.

Các kỹ thuật black-box có thể được sử dụng để tạo ra test conditions và test cases cho các chức năng của hệ thống.

Function testing được dựa trên tiêu chuẩn ISO 9126, nó tập trung vào các tiêu chí sau:

- suitability (sự phù hợp)
- interoperability (khả năng tương tác)
- security (bảo mật)
- accuracy (sự chính xác)
- compliance (tuân thủ chức năng)

Functional testing có thể thực hiện trên cả 2 cách: requirements-based và business-process-based.

### Dựa trên quy trình kinh doanh (Business-Process-Based)

Trong phương pháp này, kiểm thử chức năng tập trung vào việc kiểm tra các quy trình kinh doanh và hoạt động của hệ thống từ góc độ của người dùng cuối.

Các kịch bản kiểm thử được thiết kế dựa trên các quy trình kinh doanh cụ thể mà hệ thống phải hỗ trợ và thực hiện.

Phương pháp này nhấn mạnh vào việc đảm bảo rằng phần mềm không chỉ đáp ứng các yêu cầu chức năng mà còn hỗ trợ các quy trình kinh doanh hiệu quả.

### Dựa trên yêu cầu (Requirements-Based)

Trong phương pháp này, kiểm thử chức năng được thực hiện dựa trên các yêu cầu chức năng cụ thể đã được xác định trong tài liệu yêu cầu phần mềm.

Các kịch bản kiểm thử được thiết kế để kiểm tra xem phần mềm có đáp ứng được các yêu cầu chức năng đã được xác định hay không.

Đây là phương pháp phổ biến và hiệu quả khi có sẵn các tài liệu yêu cầu chi tiết và rõ ràng.

---

# Non-functional Testing

Kiểm thử yếu tố chất lượng, tập trung vào đánh giá hiệu suất, khả năng sử dụng, độ tin cậy và các khía cạnh phi chức năng khác của một hệ thống phần mềm.

- **KT hiệu suất**: stress/load, phản hồi, hiệu suất ổn định hệ thống dưới các điều kiện.
- **KT sử dụng**: độ thân thiện, dễ sử dụng.
- **KT bảo mật**: xác định các lỗ hổng, cơ chế bảo mật HT. Kiểm thử xác định, ủy quyền, truy cập chống hacking, truy cập trái phép.
- **KT tương thích**: hoạt động đúng nền tảng, hệ điều hành, trình duyệt, thiết bị,…
- **KT mở rộng**: duy trì, mở rộng.
- **KT tuân thủ**: khả năng tiếp cận, quy định bảo vệ data phù hợp với từng ngành cụ thể.

### Ví dụ về kiểm thử hiệu suất

Một công ty đang vận hành một trang web thương mại điện tử để bán hàng trực tuyến. Dưới đây là các bước kiểm thử hiệu suất có thể áp dụng:

1. **Xác định yêu cầu hiệu suất**: thời gian phản hồi, tải trang, người dùng đồng thời.
2. **Lập kế hoạch kịch bản kiểm thử**: dựa theo hành vi người dùng.
3. **Thiết lập môi trường kiểm thử**: giống với môi trường thật.
4. **Kiểm thử tải (Load Testing)**: dùng JMeter, Gatling hoặc LoadRunner mô phỏng tải.
5. **Kiểm thử căng thẳng (Stress Testing)**: kiểm tra điểm gãy của hệ thống.
6. **Phân tích kết quả**: xác định phần cần cải thiện.

---

# Phân loại lỗi

### Cách xác định nguyên nhân

- **Error**: hành động của con người dẫn đến kết quả sai.
- **Defect/Bug**: lỗi trong quá trình phát triển hoặc logic sai.
- **Failure**: kết quả thực tế khác với kỳ vọng.

**Summary**:

Con người gây ra error → Dẫn đến bug/defect → Khi chạy sẽ dẫn đến failure.

**Ví dụ**:

- Error: Dev code sai
- Defect/Bug: Bị lỗi API, hiển thị error msg
- Failure: Buyer không sử dụng được

Nguồn lỗi:

- Lỗi từ tài liệu (docs)
- Lỗi trong quá trình phát triển
- Lỗi trong quá trình kiểm thử
- Lỗi từ môi trường: server, thiết bị, v.v.

---

# Regression Test

## What

Regression test - Kiểm thử hồi quy đảm bảo rằng các chức năng đã được kiểm thử trước đó không bị ảnh hưởng sau khi có thay đổi.

## Why

Mỗi thay đổi nhỏ có thể ảnh hưởng lớn đến chức năng đã hoàn thiện. Cần kiểm tra đảm bảo hệ thống vẫn hoạt động trơn tru.

## When

- Khi sửa lỗi phần mềm
- Khi thêm chức năng mới
- Khi sửa đổi chức năng hiện có
- Khi nâng cao hiệu suất
- Khi thay đổi môi trường

## Who

- PO: hiểu nghiệp vụ người dùng
- Dev & Dev Lead: hiểu nghiệp vụ + cấu trúc hệ thống
- QE & QE Lead: hiểu nghiệp vụ và hệ thống

## How to Implement

### Retest All

- Chạy lại tất cả test cases.
- Ưu: đảm bảo chắc chắn.
- Nhược: mất thời gian, không thể automation hết.

### Regression Test Selection

- Chọn test case bị ảnh hưởng.
- Ưu: tối ưu.
- Nhược: phụ thuộc hiểu biết người đánh giá.

### Prioritization of Test Cases

- Chọn test case quan trọng, End User thường dùng.
- Ưu: giảm khối lượng kiểm thử.
- Nhược: khi hệ thống lớn, số lượng này vẫn rất nhiều.

### Best Practice

- Áp dụng kết hợp cả 3 cách:
  - Xác định module ảnh hưởng lớn → **Test All**
  - Ảnh hưởng nhỏ → **Test Selection**
  - Có thể bị ảnh hưởng → **Test Prioritization**
