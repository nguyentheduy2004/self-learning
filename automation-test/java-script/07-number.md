
###  Numbers trong JavaScript

Trong JavaScript, **`number`** là một kiểu dữ liệu nguyên thủy (primitive data type) được sử dụng để biểu diễn cả số nguyên (integers) và số thực (floating-point numbers).

JavaScript không phân biệt rõ ràng giữa hai loại này ở cấp độ kiểu dữ liệu cơ bản. Ngoài các toán tử số học đã học, JavaScript cung cấp các phương thức và đối tượng tích hợp sẵn để làm việc hiệu quả hơn với số.

### A. Biểu diễn số (Number Representation)

```javascript
let integerNum = 100;
let floatNum = 3.14159;
let scientificNotation = 2.5e6; // Tương đương 2.5 * 10^6 = 2500000
let negativeNum = -50;

console.log(integerNum);          // Output: 100
console.log(floatNum);            // Output: 3.14159
console.log(scientificNotation);  // Output: 2500000
console.log(negativeNum);         // Output: -50
```

**Các giá trị số đặc biệt:**
* **`Infinity`**: Đại diện cho vô cực dương (ví dụ, kết quả của `1 / 0`).
* **`-Infinity`**: Đại diện cho vô cực âm (ví dụ, kết quả của `-1 / 0`).
* **`NaN` (Not a Number)**: Đại diện cho một giá trị không phải là số hợp lệ. Thường là kết quả của một phép toán số học không xác định hoặc không thành công (ví dụ: `0 / 0`, `parseInt("abc")`, `Math.sqrt(-1)`).
```javascript
console.log(1 / 0);       // Output: Infinity
console.log(-1 / 0);      // Output: -Infinity
console.log(0 / 0);       // Output: NaN
console.log("text" * 2);  // Output: NaN
console.log(NaN === NaN); // Output: false (NaN không bằng chính nó)
```
Để kiểm tra một giá trị có phải là `NaN` hay không, sử dụng hàm `isNaN()` hoặc `Number.isNaN()`.

### B. Phương thức của đối tượng `Number` và hàm global

JavaScript cung cấp các phương thức có thể được gọi trực tiếp trên một giá trị số (thông qua prototype của `Number`) hoặc các hàm global liên quan đến số.

#### 1. `Number.isFinite(value)` (ES6)

* Kiểm tra xem một giá trị có phải là một số hữu hạn hay không (không phải `Infinity`, `-Infinity`, hoặc `NaN`).
* Trả về `true` nếu là số hữu hạn, `false` nếu không.

```javascript
console.log(Number.isFinite(123));       // Output: true
console.log(Number.isFinite(-1.23));     // Output: true
console.log(Number.isFinite(Infinity));  // Output: false
console.log(Number.isFinite(-Infinity)); // Output: false
console.log(Number.isFinite(NaN));       // Output: false
console.log(Number.isFinite("123"));     // Output: false (phải là kiểu number)
```

#### 2. `Number.isInteger(value)` (ES6)

* Kiểm tra xem một giá trị có phải là một số nguyên hay không.
* Trả về `true` nếu là số nguyên, `false` nếu không (bao gồm cả số thực, `Infinity`, `NaN`, hoặc không phải kiểu number).

```javascript
console.log(Number.isInteger(10));        // Output: true
console.log(Number.isInteger(10.0));      // Output: true (10.0 vẫn được coi là số nguyên)
console.log(Number.isInteger(10.5));      // Output: false
console.log(Number.isInteger(Infinity));  // Output: false
console.log(Number.isInteger("10"));      // Output: false
```

#### 3. `Number.isNaN(value)` (ES6)

* Kiểm tra xem một giá trị có phải là `NaN` hay không.
* Đây là phiên bản đáng tin cậy hơn hàm global `isNaN()` vì nó không thực hiện ép kiểu. `Number.isNaN(value)` chỉ trả về `true` nếu `value` thực sự là `NaN` và có kiểu `number`.

```javascript
console.log(Number.isNaN(NaN));       // Output: true
console.log(Number.isNaN(123));       // Output: false
console.log(Number.isNaN("abc"));     // Output: false (vì "abc" không phải là NaN thuộc kiểu number)
console.log(Number.isNaN(undefined)); // Output: false

// So sánh với hàm global isNaN() (ít tin cậy hơn)
console.log(isNaN("abc"));     // Output: true (vì "abc" bị ép kiểu thành NaN)
console.log(isNaN(undefined)); // Output: true (vì undefined bị ép kiểu thành NaN)
```

#### 4. `Number.parseFloat(string)` (ES6)

* Hoạt động giống hệt hàm global `parseFloat(string)`.
* Phân tích một chuỗi và trả về một số thực (floating-point number).
* Dừng phân tích khi gặp ký tự không phải là số (ngoại trừ dấu thập phân đầu tiên).

```javascript
console.log(Number.parseFloat("3.14"));      // Output: 3.14
console.log(Number.parseFloat("3.14159text")); // Output: 3.14159
console.log(Number.parseFloat("  100 px  ")); // Output: 100
console.log(Number.parseFloat("abc"));       // Output: NaN
```

#### 5. `Number.parseInt(string, radix)` (ES6)

* Hoạt động giống hệt hàm global `parseInt(string, radix)`.
* Phân tích một chuỗi và trả về một số nguyên.
* `radix` (cơ số) là một số nguyên từ 2 đến 36 chỉ định cơ số của chuỗi số. Nếu bỏ qua hoặc là 0, JavaScript sẽ cố gắng đoán (thường là 10, nhưng có thể là 16 nếu chuỗi bắt đầu bằng `0x` hoặc `0X`). **Luôn luôn chỉ định `radix` (thường là 10) để tránh hành vi không mong muốn.**

```javascript
console.log(Number.parseInt("100"));        // Output: 100 (radix mặc định thường là 10)
console.log(Number.parseInt("100", 10));    // Output: 100
console.log(Number.parseInt("10110", 2));   // Output: 22 (nhị phân)
console.log(Number.parseInt("FF", 16));     // Output: 255 (thập lục phân)
console.log(Number.parseInt("3.14"));       // Output: 3 (bỏ phần thập phân)
console.log(Number.parseInt("10 years"));   // Output: 10
console.log(Number.parseInt("age 25"));     // Output: NaN (bắt đầu bằng ký tự không phải số)
```

#### 6. `num.toFixed(digits)`

* Định dạng một số sử dụng ký pháp điểm cố định (fixed-point notation).
* Trả về một **chuỗi** biểu diễn số với `digits` chữ số sau dấu thập phân.
* Số sẽ được làm tròn nếu cần.
* `digits`: Số chữ số sau dấu thập phân (0 đến 20). Nếu bỏ qua, mặc định là 0.

```javascript
let price = 19.9956;
console.log(price.toFixed(2));  // Output: "20.00" (làm tròn lên)
console.log(price.toFixed(3));  // Output: "19.996"
console.log(price.toFixed(0));  // Output: "20"

let wholeNum = 123;
console.log(wholeNum.toFixed(2)); // Output: "123.00"
```

#### 7. `num.toPrecision(precision)`

* Định dạng một số với một độ dài (tổng số chữ số) được chỉ định.
* Trả về một **chuỗi** biểu diễn số.
* `precision`: Số lượng chữ số có nghĩa (1 đến 100).
* Nếu `precision` nhỏ hơn số chữ số phần nguyên, số sẽ được biểu diễn ở dạng khoa học (exponential notation).

```javascript
let value = 123.456789;
console.log(value.toPrecision(5));  // Output: "123.46" (5 chữ số có nghĩa, làm tròn)
console.log(value.toPrecision(3));  // Output: "123"
console.log(value.toPrecision(2));  // Output: "1.2e+2" (dạng khoa học)
console.log(value.toPrecision(10)); // Output: "123.4567890" (thêm số 0 nếu cần)

let smallNum = 0.00012345;
console.log(smallNum.toPrecision(3)); // Output: "0.000123"
console.log(smallNum.toPrecision(1)); // Output: "1e-4"
```

#### 8. `num.toString(radix)`

* Chuyển đổi một số thành chuỗi.
* `radix` (tùy chọn): Cơ số để biểu diễn số (2 đến 36). Mặc định là 10 (thập phân).

```javascript
let numToConvert = 255;
console.log(numToConvert.toString());   // Output: "255" (cơ số 10)
console.log(numToConvert.toString(16)); // Output: "ff" (thập lục phân)
console.log(numToConvert.toString(2));  // Output: "11111111" (nhị phân)
console.log(numToConvert.toString(8));  // Output: "377" (bát phân)

let floatVal = 3.14;
console.log(floatVal.toString()); // Output: "3.14"
```

### C. Đối tượng `Math`

Đối tượng `Math` là một đối tượng tích hợp sẵn trong JavaScript, chứa các thuộc tính và phương thức cho các hằng số và hàm toán học. `Math` không phải là một hàm constructor (bạn không thể tạo đối tượng `Math` bằng `new Math()`). Tất cả các thuộc tính và phương thức của `Math` đều là tĩnh (static), nghĩa là bạn gọi chúng trực tiếp trên đối tượng `Math` (ví dụ: `Math.PI`, `Math.round()`).

#### Hằng số của `Math`:
* `Math.PI`: Số Pi (π ≈ 3.14159)
* `Math.E`: Số Euler (e ≈ 2.718)
* `Math.SQRT2`: Căn bậc hai của 2 (≈ 1.414)
* ... và nhiều hằng số khác.

```javascript
console.log(Math.PI); // Output: 3.141592653589793
```

#### Phương thức phổ biến của `Math`:

* **`Math.round(x)`**: Làm tròn `x` đến số nguyên gần nhất.
    * Nếu phần thập phân là `.5`, làm tròn lên số nguyên lớn hơn.
    ```javascript
    console.log(Math.round(4.7));  // Output: 5
    console.log(Math.round(4.4));  // Output: 4
    console.log(Math.round(4.5));  // Output: 5
    console.log(Math.round(-4.5)); // Output: -4 (làm tròn lên về phía dương vô cùng)
    ```

* **`Math.ceil(x)` (Ceiling - Trần nhà)**: Làm tròn `x` lên số nguyên lớn hơn hoặc bằng `x` gần nhất.
    ```javascript
    console.log(Math.ceil(4.7));  // Output: 5
    console.log(Math.ceil(4.4));  // Output: 5
    console.log(Math.ceil(4.0));  // Output: 4
    console.log(Math.ceil(-4.2)); // Output: -4
    ```

* **`Math.floor(x)` (Floor - Sàn nhà)**: Làm tròn `x` xuống số nguyên nhỏ hơn hoặc bằng `x` gần nhất.
    ```javascript
    console.log(Math.floor(4.7));  // Output: 4
    console.log(Math.floor(4.4));  // Output: 4
    console.log(Math.floor(4.99)); // Output: 4
    console.log(Math.floor(-4.2)); // Output: -5
    ```

* **`Math.trunc(x)` (Truncate - ES6)**: Trả về phần nguyên của `x` bằng cách loại bỏ các chữ số thập phân.
    ```javascript
    console.log(Math.trunc(4.7));  // Output: 4
    console.log(Math.trunc(4.2));  // Output: 4
    console.log(Math.trunc(-4.7)); // Output: -4
    ```

* **`Math.pow(base, exponent)`**: Trả về `base` lũy thừa `exponent` (base^exponent). Tương tự toán tử `**`.
    ```javascript
    console.log(Math.pow(2, 3)); // Output: 8 (2^3)
    console.log(Math.pow(5, 2)); // Output: 25 (5^2)
    ```

* **`Math.sqrt(x)`**: Trả về căn bậc hai của `x`.
    ```javascript
    console.log(Math.sqrt(9));  // Output: 3
    console.log(Math.sqrt(2));  // Output: 1.4142135623730951
    console.log(Math.sqrt(-1)); // Output: NaN
    ```

* **`Math.abs(x)`**: Trả về giá trị tuyệt đối (phần dương) của `x`.
    ```javascript
    console.log(Math.abs(-5)); // Output: 5
    console.log(Math.abs(5));  // Output: 5
    ```

* **`Math.min(value1, value2, ...)`**: Trả về giá trị nhỏ nhất trong các số được truyền vào.
* **`Math.max(value1, value2, ...)`**: Trả về giá trị lớn nhất trong các số được truyền vào.
    ```javascript
    console.log(Math.min(0, 150, 30, 20, -8, -200)); // Output: -200
    console.log(Math.max(0, 150, 30, 20, -8, -200)); // Output: 150

    // Để tìm min/max trong một mảng, sử dụng spread operator (...)
    let numbersArray = [10, 5, 25, -2, 100];
    console.log(Math.min(...numbersArray)); // Output: -2
    console.log(Math.max(...numbersArray)); // Output: 100
    ```

* **`Math.random()`**:
    * Trả về một số thực ngẫu nhiên trong khoảng `[0, 1)` (bao gồm 0, nhưng không bao gồm 1).
    ```javascript
    console.log(Math.random()); // Output: một số ngẫu nhiên, ví dụ 0.123456789
    console.log(Math.random()); // Output: một số ngẫu nhiên khác
    ```
    * **Tạo số nguyên ngẫu nhiên trong một khoảng `[min, max]`:**
        ```javascript
        function getRandomInt(min, max) {
            min = Math.ceil(min);
            max = Math.floor(max);
            return Math.floor(Math.random() * (max - min + 1)) + min;
        }
        console.log(getRandomInt(1, 10)); // Output: một số nguyên ngẫu nhiên từ 1 đến 10
        console.log(getRandomInt(50, 100)); // Output: một số nguyên ngẫu nhiên từ 50 đến 100
        ```

### D. Ứng dụng trong testing (Applications in Testing)

Kiểm tra các giá trị số là một phần phổ biến trong kiểm thử phần mềm, đặc biệt là QE.
* **Kiểm tra giá tiền (Prices):**
    * Giá sản phẩm có đúng không?
    * Tổng tiền trong giỏ hàng có được tính toán chính xác không?
    * Giảm giá có được áp dụng đúng không?
    * Định dạng tiền tệ có đúng không (ví dụ, sử dụng `toFixed(2)` để kiểm tra số chữ số thập phân).
    ```javascript
    // Ví dụ test case (giả định)
    let productPrice = 19.99;
    let quantity = 3;
    let discount = 0.1; // 10%
    let expectedTotalPrice = (productPrice * quantity * (1 - discount)).toFixed(2);

    // (Trong framework test, bạn sẽ có hàm assert)
    // pseudoAssert.assertEqual(calculatedTotalPrice.toFixed(2), expectedTotalPrice, "Total price calculation is correct");
    ```
* **Kiểm tra điểm số (Scores), số lượng (Quantities), chỉ số (Metrics):**
    * Điểm số người dùng có nằm trong khoảng hợp lệ không?
    * Số lượng sản phẩm trong kho có được cập nhật đúng không?
    * Các chỉ số hiệu suất, thống kê có chính xác không?
    * Sử dụng `Math.round()`, `Math.floor()`, `Math.ceil()` để xử lý các giá trị cần làm tròn.
* **Kiểm tra dữ liệu ngẫu nhiên (Random Data):**
    * Khi test các tính năng sử dụng dữ liệu ngẫu nhiên, đảm bảo rằng các giá trị nằm trong phạm vi mong đợi (sử dụng `Math.random()` kết hợp với các phép toán để giới hạn khoảng).
* **Chuyển đổi và xác thực (Conversion and Validation):**
    * Khi nhận dữ liệu từ API hoặc input của người dùng (thường là chuỗi), cần chuyển đổi sang số (`parseInt`, `parseFloat`) và xác thực xem có phải là số hợp lệ không (`Number.isNaN`, `Number.isFinite`).
