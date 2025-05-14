
###  Hàm trong JavaScript

1. **Khai Báo Hàm (Function Declaration)**:
   - Hàm trong JavaScript giúp modular hóa code và tái sử dụng các tác vụ.
   - **Ví dụ 1**: Hàm không có tham số, không trả về giá trị
     ```javascript
     function greet() {
         console.log("Hello, World!");
     }
     greet(); // Output: Hello, World!
     ```
   - **Ví dụ 2**: Hàm có tham số, không trả về giá trị
     ```javascript
     unction greetPerson(person) {
         console.log(`Hello, ${person}!`);
     }
     greetPerson("Alice"); // Output: Hello, Alice!
     greetPerson("Bob"); // Output: Hello, Bob!
     ```
   - **Ví dụ 3**: Hàm có tham số, có trả về giá trị
     ```javascript
     function multiply(a, b) {
         return a * b;
     }
     let result = multiply(3, 4);
     console.log("Product:", result); // Output: Product: 12
     ```
   - **Function Hoisting**:
     Các hàm khai báo bằng từ khóa `function` sẽ được hoisted lên đầu scope của chúng, cho phép bạn gọi hàm trước khi khai báo.
     ```javascript
     sayHi(); // Output: Hi there!
     function sayHi() {
         console.log("Hi there!");
     }
     ```

2. **Arrow Functions (Hàm Mũi Tên)**:
   - Cung cấp cú pháp ngắn gọn và hành vi khác biệt so với `function declarations`.
   - **Cú pháp**:
     ```javascript
     const multiply = (a, b) => a * b;
     console.log(multiply(2, 3)); // Output: 6
     ```
   - **Ví dụ**: Hàm không có tham số
     ```javascript
     const printMessage = () => {
         console.log("This is an arrow function.");
     };
     printMessage(); // Output: This is an arrow function.
     ```

3. **Tham Số (Parameters) và Đối Số (Arguments)**:
   - **Parameters** là các tên biến được định nghĩa trong hàm.
   - **Arguments** là các giá trị thực tế khi hàm được gọi.
   - **Ví dụ**:
     ```javascript
     function calculateArea(length, width) {
         return length * width;
     }
     console.log("Diện tích:", calculateArea(10, 5)); // Output: Diện tích: 50
     ```

4. **Default Parameters**:
   - Gán giá trị mặc định cho các tham số trong hàm.
   - **Ví dụ**:
     ```javascript
     function greetWithDefault(name = "Guest", greeting = "Hello") {
         console.log(`${greeting}, ${name}!`);
     }
     greetWithDefault("Alice"); // Output: Hello, Alice!
     greetWithDefault();        // Output: Hello, Guest!
     greetWithDefault("Alice", "Hi"); // Output: Hi, Alice!
     ```

5. **Rest Parameters**:
   - Cho phép một hàm chấp nhận số lượng arguments không xác định dưới dạng một mảng.
   - **Ví dụ**:
     ```javascript
     function sumAll(...numbers) {
         let total = 0;
         for (const num of numbers) {
             total += num;
         }
         return total;
     }
     console.log(sumAll(1, 2, 3, 4)); // Output: 10
     ```

6. **The `arguments` Object**:
   - Dành cho hàm khai báo bằng `function` truyền thống, chứa tất cả arguments của hàm.
   - **Ví dụ**:
     ```javascript
     function logAllArguments() {
         console.log("Number of arguments:", arguments.length);
         for (let i = 0; i < arguments.length; i++) {
             console.log(`Argument ${i}: ${arguments[i]}`);
         }
     }
     logAllArguments("apple", "banana", 123);
     /*
     Output:
     Number of arguments: 3
     Argument 0: apple
     Argument 1: banana
     Argument 2: 123
     */
     ```

7. **Giá Trị Trả Về (Return Values)**:
   - Hàm có thể trả về một giá trị bằng từ khóa `return`.
   - **Ví dụ**: Trả về một object từ hàm
     ```javascript
     function getUserDetails(id) {
         if (id === 1) {
             return {
                 name: "Alice Wonderland",
                 email: "alice@example.com",
                 isActive: true
             };
         }
         return null;
     }
     const user = getUserDetails(1);
     console.log(user.name); // Output: Alice Wonderland
     ```
