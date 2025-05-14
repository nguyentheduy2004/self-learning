
# Key Takeaways: JavaScript Operators, Data Types, and Type Conversion

### A. **Arithmetic Operators**
Các toán tử số học được sử dụng để thực hiện các phép toán trên số (có thể là số nguyên hoặc biến).

| Operator | Description                  | Example                | Result (For `let x = 10, y = 3;`) |
|----------|------------------------------|------------------------|----------------------------------|
| `+`      | Addition                     | `x + y`                | `13`                             |
| `-`      | Subtraction                  | `x - y`                | `7`                              |
| `*`      | Multiplication               | `x * y`                | `30`                             |
| `/`      | Division                     | `x / y`                | `3.333...`                       |
| `%`      | Modulus (remainder)          | `x % y`                | `1`                              |
| `**`     | Exponentiation (ES2016)      | `x ** y` (10^3)        | `1000`                           |
| `++`     | Increment                    | `x++` (post-increment) | `x` becomes `11`                 |
| `--`     | Decrement                    | `y--` (post-decrement) | `y` becomes `2`                  |

- **Post-increment (`variable++`)** trả về giá trị *trước* khi tăng:
    ```javascript
    let a = 5;
    let b = a++; // b gets a value of 5, then a becomes 6
    console.log(`a: ${a}, b: ${b}`); // Output: a: 6, b: 5
    ```

- **Pre-increment (`++variable`)** tăng giá trị *trước* khi trả về giá trị đó:
    ```javascript
    let c = 5;
    let d = ++c; // c becomes 6, then d gets the value 6
    console.log(`c: ${c}, d: ${d}`); // Output: c: 6, d: 6
    ```

**Operator Precedence:** JavaScript tuân theo một thứ tự hoạt động cụ thể. Sử dụng dấu ngoặc đơn để thay đổi thứ tự:
```javascript
let result = 10 + 5 * 2; // Multiplication before addition: 10 + 10 = 20
console.log(result); // Output: 20

let anotherResult = (10 + 5) * 2; // Parentheses first: 15 * 2 = 30
console.log(anotherResult); // Output: 30
```

---

### B. **Comparison Operators**
Toán tử so sánh được sử dụng để so sánh hai giá trị và trả về kết quả `boolean` (`true` hoặc `false`).

| Operator | Description                         | Example (`let val1 = 5, val2 = "5", val3 = 10;`) | Result         |
|----------|-------------------------------------|---------------------------------------------------|----------------|
| `==`     | Equal to (compares value, with coercion) | `val1 == val2` (5 == "5")                     | `true`         |
| `===`    | Strict equal to (compares value and type) | `val1 === val2` (5 === "5")                   | `false`        |
| `!=`     | Not equal to (with coercion)           | `val1 != val3` (5 != 10)                      | `true`         |
| `!==`    | Strict not equal to (without coercion)  | `val1 !== val2` (5 !== "5")                   | `true`         |
| `>`      | Greater than                         | `val3 > val1` (10 > 5)                        | `true`         |
| `<`      | Less than                            | `val1 < val3` (5 < 10)                        | `true`         |
| `>=`     | Greater than or equal to             | `val1 >= val2` (5 >= "5")                     | `true`         |
| `<=`     | Less than or equal to                | `val3 <= val1` (10 <= 5)                      | `false`        |

- **`==` (Loose Equality)** thực hiện ép kiểu. Ví dụ:
    ```javascript
    console.log(5 == "5");     // true (string "5" coerced to number 5)
    console.log(true == 1);    // true (boolean true coerced to number 1)
    console.log(null == undefined); // true (special case)
    ```

- **`===` (Strict Equality)** không thực hiện ép kiểu. Ví dụ:
    ```javascript
    console.log(5 === "5");    // false (number vs string)
    console.log(true === 1);   // false (boolean vs number)
    console.log(null === undefined); // false
    ```

---

### C. **Logical Operators**
Các toán tử logic được sử dụng để kết hợp hoặc phủ định các biểu thức boolean.

| Operator | Description              | Example (`let a = true, b = false;`) | Result  |
|----------|--------------------------|--------------------------------------|---------|
| `&&`     | Logical AND (returns true if both are true)  | `a && b`                              | `false` |
| `||`     | Logical OR (returns true if at least one is true) | `a || b`                             | `true`  |
| `!`      | Logical NOT (negates the boolean) | `!a`                                 | `false` |

- **`&&` (AND):** Trả về `true` nếu *both* toán hạng đều `true`.
    ```javascript
    console.log(true && true);   // true
    console.log(true && false);  // false
    console.log(false && true);  // false
    ```

- **`||` (OR):** Trả về `true` nếu *ít nhất một toán hạng là true* (truthy). Nếu cả hai toán hạng đều là falsy, nó trả về `false`.
    ```javascript
    console.log(true || true);   // true
    console.log(true || false);  // true
    console.log(false || true);  // true
    console.log(false || false); // false
    ```

- **`!` (NOT):** Đảo ngược giá trị boolean.
    ```javascript
    console.log(!true);  // false
    console.log(!false); // true
    ```

**Truthy and Falsy Values:**
Trong JavaScript, các giá trị khác ngoài `false` và `0` có thể được coi là`truthy` (true) or `falsy` (false):
- **Falsy values** bao gồm: `false`, `0`, `-0`, `""`, `null`, `undefined`, `NaN`.
- **Truthy values** bao gồm: Bất kỳ giá trị nào không được coi là sai, chẳng hạn như`"hello"`, `42`, `{}`, `[]`.

```javascript
if ("some string") { // truthy
    console.log("This is truthy");
}

if (0) { // falsy
    console.log("This won't run");
} else {
    console.log("0 is falsy");
}
```

---

### D. **Advanced Data Types**

1. **Arrays**
    1. **Cơ Bản về Mảng**:
   - Mảng là một cấu trúc dữ liệu dùng để lưu trữ nhiều giá trị dưới một tên biến, các phần tử trong mảng được đánh chỉ số bắt đầu từ `0`.
   - **Ví dụ**:
     ```javascript
     let fruits = ["Apple", "Banana", "Orange"];
     console.log(fruits[0]);  // Output: "Apple"
     ```

    2. **Tạo Mảng**:
   - **Array Literals** (Cách tạo mảng phổ biến):
     ```javascript
     let fruits = ["Apple", "Banana", "Orange"];
     console.log(fruits);  // Output: ["Apple", "Banana", "Orange"]
     ```
   - **Sử dụng `new Array()`** có thể tạo mảng với kích thước hoặc các phần tử cụ thể.
     ```javascript
     let arr1 = new Array(5);  // Tạo mảng có 5 phần tử rỗng
     console.log(arr1);         // Output: [ <5 empty items> ]
     let arr2 = new Array("Red", "Green", "Blue");
     console.log(arr2);         // Output: ["Red", "Green", "Blue"]
     ```

    3. **Truy Cập và Thay Đổi Phần Tử Của Mảng**:
   - **Truy Cập**: Sử dụng chỉ số của mảng để lấy phần tử.
     ```javascript
     let colors = ["Red", "Green", "Blue"];
     console.log(colors[1]);  // Output: "Green"
     ```
   - **Thay Đổi**: Gán giá trị mới cho chỉ số của mảng.
     ```javascript
     colors[1] = "Purple";
     console.log(colors);  // Output: ["Red", "Purple", "Blue"]
     ```

    4. **Các Thuộc Tính và Phương Thức Thông Dụng**:
   - **`length`**: Lấy số lượng phần tử trong mảng.
     ```javascript
     let fruits = ["Apple", "Banana", "Orange"];
     console.log(fruits.length);  // Output: 3
     ```
   - **Thêm và Xóa Phần Tử**:
     - **`push()`**: Thêm phần tử vào cuối mảng.
       ```javascript
       let animals = ["Dog", "Cat"];
       animals.push("Bird");
       console.log(animals);  // Output: ["Dog", "Cat", "Bird"]
       ```
     - **`pop()`**: Xóa phần tử cuối cùng trong mảng.
       ```javascript
       let tasks = ["Task1", "Task2", "Task3"];
       let removedTask = tasks.pop();
       console.log(tasks);      // Output: ["Task1", "Task2"]
       console.log(removedTask); // Output: "Task3"
       ```
     - **`shift()`**: Xóa phần tử đầu tiên trong mảng.
       ```javascript
       let queue = ["A", "B", "C"];
       let firstItem = queue.shift();
       console.log(queue);      // Output: ["B", "C"]
       console.log(firstItem);  // Output: "A"
       ```

    5. **Sao Chép và Nối Mảng**:
   - **`slice()`**: Tạo bản sao hoặc một phần của mảng.
     ```javascript
     let original = [1, 2, 3, 4, 5];
     let copy = original.slice();
     console.log(copy);  // Output: [1, 2, 3, 4, 5]
     ```
   - **Spread Operator (`...`)**: Sao chép hoặc nối mảng.
     ```javascript
     let arrA = [1, 2, 3];
     let arrB = [4, 5, 6];
     let combined = [...arrA, ...arrB];
     console.log(combined);  // Output: [1, 2, 3, 4, 5, 6]
     ```
   - **`concat()`**: Nối các mảng với nhau.
     ```javascript
     let array1 = [1, 2];
     let array2 = [3, 4];
     let combinedArray = array1.concat(array2);
     console.log(combinedArray);  // Output: [1, 2, 3, 4]
     ```

    6. **Tìm Kiếm Phần Tử trong Mảng**:
   - **`indexOf()`**: Tìm chỉ số của phần tử đầu tiên trong mảng.
     ```javascript
     let numbers = [10, 20, 30, 40];
     console.log(numbers.indexOf(30));  // Output: 2
     ```
   - **`includes()`**: Kiểm tra xem phần tử có tồn tại trong mảng hay không.
     ```javascript
     console.log(numbers.includes(20));  // Output: true
     console.log(numbers.includes(50));  // Output: false
     ```

    7. **Lặp Qua Các Phần Tử Của Mảng**:
   - **`forEach()`**: Thực thi một hàm cho mỗi phần tử trong mảng.
     ```javascript
     let names = ["Alice", "Bob", "Charlie"];
     names.forEach(function(name, index) {
         console.log(`${index}: ${name}`);
     });
     // Output: 
     // 0: Alice
     // 1: Bob
     // 2: Charlie
     ```
   - **`map()`**: Tạo một mảng mới bằng cách thay đổi mỗi phần tử.
     ```javascript
     let nums = [1, 2, 3, 4];
     let squared = nums.map(function(num) {
         return num * num;
     });
     console.log(squared);  // Output: [1, 4, 9, 16]
     ```
   - **`filter()`**: Tạo mảng mới chứa các phần tử thỏa mãn điều kiện.
     ```javascript
     let scores = [80, 45, 92, 67];
     let passingScores = scores.filter(function(score) {
         return score >= 60;
     });
     console.log(passingScores);  // Output: [80, 92, 67]
     ```

    8. **Các Phương Thức Khác**:
   - **`reverse()`**: Đảo ngược thứ tự các phần tử trong mảng.
     ```javascript
     let numbers = [1, 2, 3, 4];
     numbers.reverse();
     console.log(numbers);  // Output: [4, 3, 2, 1]
     ```
   - **`sort()`**: Sắp xếp các phần tử trong mảng. Cần sử dụng hàm so sánh khi sắp xếp số.
     ```javascript
     let unsorted = [40, 100, 1, 5];
     unsorted.sort(function(a, b) {
         return a - b;  // Sắp xếp tăng dần
     });
     console.log(unsorted);  // Output: [1, 5, 40, 100]
     ```

2. **Objects**
    1. **Cơ Bản về Mảng**:
   - Objects trong JavaScript là một kiểu dữ liệu tham chiếu, dùng để lưu trữ các tập hợp dữ liệu phức tạp và các thực thể có cấu trúc. Một object gồm các cặp `key-value` (khóa-giá trị), trong đó key là thuộc tính và value có thể là bất kỳ kiểu dữ liệu nào, bao gồm cả object và array khác.

    2. **Tạo Object**:
   - **Object Literal**: Cách phổ biến nhất để tạo object trong JavaScript, sử dụng dấu ngoặc nhọn `{}` và các cặp `key: value`.
     ```javascript
     let user = {
         firstName: "John",
         lastName: "Doe",
         age: 30,
         greet: function() {
             console.log("Hello, my name is " + this.firstName);
         }
     };
     user.greet();  // Output: Hello, my name is John
     ```
   - **Sử dụng `new Object()`**: Một cách khác để tạo object nhưng ít phổ biến hơn.
     ```javascript
     let car = new Object();
     car.make = "Toyota";
     car.model = "Camry";
     console.log(car);  // Output: { make: "Toyota", model: "Camry" }
     ```

    3. **Truy Cập Thuộc Tính của Object**:
   - **Dot Notation**: Dễ sử dụng khi tên thuộc tính là hợp lệ (không chứa ký tự đặc biệt hoặc khoảng trắng).
     ```javascript
     let book = {
         title: "The Lord of the Rings",
         author: "J.R.R. Tolkien"
     };
     console.log(book.title);  // Output: The Lord of the Rings
     ```
   - **Bracket Notation**: Dùng dấu ngoặc vuông, có thể truy cập các thuộc tính có tên đặc biệt hoặc là biến.
     ```javascript
     let book = { "book title": "The Lord of the Rings" };
     console.log(book["book title"]);  // Output: The Lord of the Rings
     ```

    4. **Thêm, Sửa và Xóa Thuộc Tính**:
   - **Thêm thuộc tính mới**: Sử dụng dot notation hoặc bracket notation để thêm thuộc tính vào object.
     ```javascript
     let person = { name: "Alice" };
     person.age = 25;
     console.log(person);  // Output: { name: "Alice", age: 25 }
     ```
   - **Sửa thuộc tính**: Gán lại giá trị mới cho một thuộc tính đã tồn tại.
     ```javascript
     person.age = 26;
     console.log(person);  // Output: { name: "Alice", age: 26 }
     ```
   - **Xóa thuộc tính**: Dùng toán tử `delete` để xóa thuộc tính khỏi object.
     ```javascript
     delete person.age;
     console.log(person);  // Output: { name: "Alice" }
     ```

    5. **Methods trong Object**:
   - Các phương thức (method) trong object là các hàm được khai báo là thuộc tính của object.
     ```javascript
     let calculator = {
         operand1: 0,
         operand2: 0,
         setOperands(a, b) {
             this.operand1 = a;
             this.operand2 = b;
         },
         add() {
             return this.operand1 + this.operand2;
         }
     };
     calculator.setOperands(10, 5);
     console.log(calculator.add());  // Output: 15
     ```

    6. **Lặp qua Thuộc Tính của Object**:
   - Sử dụng vòng lặp `for...in` để lặp qua các thuộc tính của object.
     ```javascript
     let carDetails = { make: "Honda", model: "Civic", year: 2020 };
     for (let key in carDetails) {
         console.log(`${key}: ${carDetails[key]}`);
     }
     // Output: make: Honda, model: Civic, year: 2020
     ```

    7. **Các Phương Thức Object Tích Hợp**:
   - **`Object.keys(obj)`**: Trả về một mảng chứa các key (thuộc tính) của object.
     ```javascript
     let student = { name: "Eve", age: 22 };
     console.log(Object.keys(student));  // Output: ["name", "age"]
     ```
   - **`Object.values(obj)`**: Trả về một mảng chứa các giá trị của các thuộc tính trong object.
     ```javascript
     console.log(Object.values(student));  // Output: ["Eve", 22]
     ```
   - **`Object.entries(obj)`**: Trả về mảng chứa các cặp `[key, value]` của object.
     ```javascript
     console.log(Object.entries(student));  // Output: [["name", "Eve"], ["age", 22]]
     ```

    8. **Shallow Copy và Merge Object**:
   - **`Object.assign(target, ...sources)`**: Sao chép các thuộc tính từ object nguồn vào object đích.
     ```javascript
     let target = { a: 1 };
     let source = { b: 2 };
     Object.assign(target, source);
     console.log(target);  // Output: { a: 1, b: 2 }
     ```

    9. **Đóng Băng Object**:
   - **`Object.freeze()`**: Đóng băng một object, không thể thêm, sửa hoặc xóa thuộc tính.
     ```javascript
     let settings = { volume: 50, theme: "dark" };
     Object.freeze(settings);
     settings.volume = 70; // Không có tác dụng
     console.log(settings);  // Output: { volume: 50, theme: "dark" }
     ```
    

---

### E. **Type Conversion / Type Coercion**

1. **Implicit Type Coercion**
    - JavaScript thực hiện chuyển đổi kiểu tự động trong một số trường hợp nhất định, chẳng hạn như khi sử dụng toán tử `+` với chuỗi và số.

    ```javascript
    console.log("5" + 3);  // "53" (number coerced to string)
    console.log("5" - 3);  // 2 (string coerced to number)
    ```

2. **Explicit Type Conversion**
    - CCó thể chuyển đổi kiểu dữ liệu theo cách thủ công bằng các phương pháp tích hợp sẵn.
    - **String Conversion:**
        ```javascript
        let num = 123;
        let strNum = String(num);
        console.log(strNum); // Output: "123"
        ```

    - **Number Conversion:**
        ```javascript
        let str = "123.45";
        let num = Number(str);
        console.log(num); // Output: 123.45
        ```

    - **Boolean Conversion:**
        ```javascript
        let truthyValue = "hello";
        let falsyValue = 0;
        console.log(Boolean(truthyValue)); // Output: true
        console.log(Boolean(falsyValue));  // Output: false
        ```

---
