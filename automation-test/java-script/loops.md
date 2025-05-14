
###  Vòng Lặp trong JavaScript

1. **Vòng Lặp là gì?**
   - **Loops** trong JavaScript là một cấu trúc điều khiển dòng chảy cơ bản, cho phép bạn chạy một khối mã nhiều lần. Điều này hữu ích khi bạn cần lặp lại hành động hoặc thực hiện tác vụ trên một tập hợp dữ liệu.

2. **Vòng Lặp `for`**:
   - Vòng lặp `for` là lựa chọn phổ biến khi bạn biết trước số lần lặp hoặc khi bạn cần lặp qua các phần tử của một tập hợp có chỉ số (như mảng hoặc chuỗi).
   - **Cú pháp**:
     ```javascript
     for (initialization; condition; finalExpression) {
         // code block to be executed
     }
     ```
   - **Ví dụ 1: Tính tổng các số từ 1 đến 10**
     ```javascript
     let sum = 0;
     for (let i = 1; i <= 10; i++) {
         sum += i;
     }
     console.log("Tổng các số từ 1 đến 10 là:", sum);  // Output: 55
     ```
   - **Ví dụ 2: In các số chẵn từ 2 đến 20**
     ```javascript
     for (let i = 2; i <= 20; i += 2) {
         console.log("Số chẵn:", i);
     }
     /*
     Output:
     Số chẵn: 2
     Số chẵn: 4
     Số chẵn: 6
     ...
     */
     ```

3. **Vòng Lặp `while`**:
   - Vòng lặp `while` lặp lại một khối mã chừng nào điều kiện được chỉ định vẫn còn `true`.
   - **Cú pháp**:
     ```javascript
     while (condition) {
         // code block to be executed
     }
     ```
   - **Ví dụ: In các số nhỏ hơn 50 và chia cho 5**
     ```javascript
     let number = 5;
     while (number < 50) {
         console.log("Số chia cho 5:", number);
         number += 5; // Tăng giá trị của number thêm 5
     }
     /*
     Output:
     Số chia cho 5: 5
     Số chia cho 5: 10
     Số chia cho 5: 15
     ...
     */
     ```

4. **Vòng Lặp `do...while`**:
   - Vòng lặp `do...while` giống như `while`, nhưng luôn chạy ít nhất một lần dù điều kiện ban đầu có là `false`.
   - **Cú pháp**:
     ```javascript
     do {
         // code block to be executed
     } while (condition);
     ```
   - **Ví dụ: In số ít nhất một lần**
     ```javascript
     let nnum = 0;
     do {
         console.log("Another number:", nnum);
         nnum++;
     } while (num < 3);
     /*
     Output:
     Another number: 0
     Another number: 1
     Another number: 2
     */
     ```

5. **Câu Lệnh Điều Khiển Vòng Lặp**:
   - **`break`**: Thoát khỏi vòng lặp ngay lập tức.
   - **`continue`**: Bỏ qua phần còn lại của lần lặp hiện tại và chuyển sang lần lặp tiếp theo.
   - **Ví dụ `break`**:
     ```javascript
     for (let i = 0; i < 5; i++) {
         if (i === 3) {
             console.log("Breaking loop at i =", i);
             break; // Thoát khỏi vòng lặp khi i = 3
         }
         console.log("Current i:", i);
     }
     /*
     Output:
     Current i: 0
     Current i: 1
     Current i: 2
     Breaking loop at i = 3
     After the loop
     */
     ```
   - **Ví dụ `continue`**:
     ```javascript
     for (let i = 0; i < 5; i++) {
         if (i % 2 === 0) {
             continue;
         }
         console.log("Odd number:", i);
     }
     /*
     Output:
     Odd number: 1
     Odd number: 3
     */
     ```

6. **Các Loại Vòng Lặp Khác**:
   - **`for...of`** : Lặp qua các giá trị của một iterable (mảng, chuỗi, Set, v.v).
     ```javascript
     const numbers = [10, 20, 30, 40];
     for (const num of numbers) {
         console.log(num);
     }
     /*
     Output:
     10
     20
     30
     40
     */
     ```
   - **`for...in`**: Lặp qua các thuộc tính có thể đếm được (enumerable properties) của một object.
     ```javascript
     const student = { name: "Alice", age: 22 };
     for (const key in student) {
         console.log(`${key}: ${student[key]}`);
     }
     /*
     Output:
     name: Alice
     age: 22
     */
     ```
