
### Câu Lệnh Điều Kiện và Toán Tử 3 Ngôi trong JavaScript

1. **Câu Lệnh `if`**:
   - Câu lệnh `if` sẽ chạy một khối mã nếu điều kiện được chỉ định là `true`.
   - **Ví dụ**:
     ```javascript
     let age = 20;
     if (age >= 18) {
         console.log("tuổi trưởng thành."); // Output: tuổi trưởng thành.
     }
     let temperature = 30;
     if (temperature > 25) {
         console.log("Trời nóng"); // Output: Trời nóng
     }
     ```

2. **Câu Lệnh `if...else`**:
   - Câu lệnh `if...else` chạy khối mã nếu điều kiện là `true` và chạy khối mã khác nếu điều kiện là `false`.
   - **Ví dụ**:
     ```javascript
     let userLoggedIn = false;
     if (userLoggedIn) {
         console.log("Chào mừng quay trở lại!");
     } else {
         console.log("Vui lòng đăng nhập."); // Output: Vui lòng đăng nhập.
     }
     ```

3. **Câu Lệnh `if...else if...else`**:
   - Câu lệnh `if...else if...else` kiểm tra nhiều điều kiện một cách tuần tự.
   - **Ví dụ: Phân loại điểm số**:
     ```javascript
     let grade = 85;
     let letterGrade;
     if (grade >= 90) {
         letterGrade = "A";
     } else if (grade >= 80) {
         letterGrade = "B"; // Điều kiện này (85 >= 80) là true
     } else if (grade >= 70) {
         letterGrade = "C";
     } else {
         letterGrade = "F";
     }
     console.log(`Điểm chữ của bạn là: ${letterGrade}`); // Output: Điểm chữ của bạn là: B
     ```

4. **Toán Tử 3 Ngôi (Ternary Operator)**:
   - Toán tử 3 ngôi là cách viết tắt cho câu lệnh `if...else` đơn giản.
   - **Cú pháp**:
     ```javascript
     condition ? expressionIfTrue : expressionIfFalse;
     ```
   - **Ví dụ**:
     ```javascript
     let age = 20;
     let canVote = (age >= 18) ? "Có thể bỏ phiếu" : "Không thể bỏ phiếu";
     console.log(canVote); // Output: Có thể bỏ phiếu
     ```

5. **Câu Lệnh `switch...case`**:
   - Câu lệnh `switch...case` cho phép bạn thực hiện các hành động khác nhau tùy vào giá trị của một biểu thức.
   - **Ví dụ 1: Kiểm tra ngày trong tuần**:
     ```javascript
     let dayNumber = new Date().getDay();
     let dayName;
     switch (dayNumber) {
         case 0:
             dayName = "Chủ Nhật";
             break;
         case 1:
             dayName = "Thứ Hai";
             break;
         //... các ngày còn lại
         default:
             dayName = "Ngày không hợp lệ";
     }
     console.log(`Hôm nay là: ${dayName}`);
     ```
   - **Ví dụ 2: Xử lý trạng thái đơn hàng**:
     ```javascript
     let orderStatus = "shipped";
     let actionMessage;
     switch (orderStatus) {
         case "pending":
             actionMessage = "Đơn hàng đang chờ xử lý.";
             break;
         case "shipped":
             actionMessage = "Đơn hàng đã được gửi đi."; // Output
             break;
         default:
             actionMessage = "Trạng thái đơn hàng không xác định.";
     }
     console.log(actionMessage);
     ```

6. **Ví Dụ Về "Fall-through" (Khi Thiếu `break`)**:
   - Nếu không có `break`, việc run sẽ "fall through" (tiếp tục chạy các `case` tiếp theo).
   - **Ví dụ**:
     ```javascript
     let fruit = "apple";
     switch (fruit) {
         case "apple":
             console.log("Apple is a fruit."); // Output
         case "banana":
             console.log("Banana is also a fruit."); // Output (do fall-through)
             break;
         default:
             console.log("Unknown fruit.");
     }
     ```
